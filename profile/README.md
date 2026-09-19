# TSU Design Patterns

This GitHub organization hosts learning materials and Java examples for students of **TSU — Tbilisi State University**. Its 14-week course teaches all 23 classic Gang of Four (GoF) object-oriented design patterns, alongside the OOP concepts and design principles needed to use them effectively. Students learn to recognize recurring design problems, compare solutions, and write software that is easier to change, test, and understand.

New patterns are introduced every week. Related patterns are grouped by the problems they solve, and later lessons build on concepts and structures introduced earlier.

## Learning outcomes

By the end of the course, students should be able to:

- Explain a pattern's intent, collaborators, trade-offs, and appropriate use cases.
- Apply OOP and SOLID principles to identify and improve fragile designs.
- Implement and test patterns in Java, using interfaces and composition effectively.
- Distinguish patterns with similar structures but different purposes.
- Refactor working code without changing its observable behavior.
- Justify when a pattern is useful and when a simpler solution is sufficient.

## Prerequisites and course format

Students should already understand basic programming: variables, control flow, methods, and simple data structures. Prior exposure to classes and objects is helpful. Week 1 provides a focused Java and OOP refresher; it is not a complete introductory programming course.

Each week combines a concept session with a guided Java lab and a short independent exercise. Examples begin with a concrete problem, examine a straightforward implementation, and introduce a pattern in response to an actual requirement or source of change. Students practice reading small UML class diagrams and verifying behavior with unit tests.

Java is the implementation language throughout. Early exercises use plain Java so the object relationships remain visible. Collections, generics, exceptions, and lambdas are introduced or revisited when needed; frameworks are not required. Git and GitHub support source control, exercise submissions, and design reviews.

## What are design patterns?

A design pattern is a named, reusable approach to a recurring design problem in a particular context. It describes responsibilities and collaboration between objects or classes, rather than providing code to copy into every application. Patterns give developers a shared vocabulary, but each introduces trade-offs and can add unnecessary complexity if applied without a reason.

This course focuses on the 23 classic GoF object-oriented design patterns. These are organized by **purpose**:

| Category | Main question | Purpose |
| --- | --- | --- |
| **Creational** | How should objects be created? | Separate construction decisions from the code that uses objects. |
| **Structural** | How should objects and classes fit together? | Compose parts into useful structures and manage their interfaces and dependencies. |
| **Behavioral** | How should responsibilities and interactions be organized? | Coordinate behavior, algorithms, and communication. |

Patterns can also be described by **scope**: class patterns rely primarily on inheritance, while object patterns rely primarily on object composition. Category describes the problem being solved; scope describes the main mechanism. These are different dimensions, not competing classifications.

## 14-week agenda

| Week | Theme and patterns | Concepts and discussion | Practical work |
| --- | --- | --- | --- |
| **1** | **Foundations + Strategy** (behavioral) | What patterns are, why they exist, their categories and scope. Java and OOP refresher. Introduce SOLID and the principles listed below. Use Strategy to make interchangeable behavior explicit. | Run a small Java program, read a class diagram, and replace a pricing-policy conditional with an interface and two strategies. Write a basic behavior test. |
| **2** | **Algorithm structure: Template Method** (behavioral) | Define an algorithm skeleton with overridable steps and hooks. Compare inheritance-based customization with Week 1's Strategy. Revisit substitutability and the open/closed principle. | Implement a report-processing workflow with Template Method, then compare it with a Strategy-based implementation. |
| **3** | **Factory Method + Abstract Factory** (creational) | Separate creation from use; distinguish an overridable creation method from factories for compatible product families. Explain how a simple factory differs from the GoF Factory Method pattern. | Add alternative document exporters, then create compatible exporter and formatter families without changing client logic. |
| **4** | **Construction and copying: Builder + Prototype** (creational) | Construct complex objects step by step or create them by copying configured instances. Discuss validation, valid object state, and shallow versus deep copies. Compare explicit copy methods and constructors with Java's cloning mechanism. | Build a validated document configuration and create variants from a prototype. Test that copies do not unintentionally share mutable state. |
| **5** | **Instance control and sharing: Singleton + Flyweight** (creational / structural) | Distinguish controlling a class's instance count from sharing reusable fine-grained objects. Examine Singleton's lifecycle, testability, and concurrency concerns; compare with explicit dependency injection. Separate Flyweight's intrinsic and extrinsic state. | Implement a small Singleton example and examine its testing costs. Build a cache of immutable text styles shared by document characters, keeping character positions external. |
| **6** | **Interface boundaries: Adapter + Facade** (structural) | Translate an incompatible interface versus provide a simpler entry point to a subsystem. Introduce dependency boundaries and the principle of least knowledge. | Adapt a legacy library interface and expose a small facade for a multi-step enrollment operation. |
| **7** | **Object wrappers: Decorator + Proxy** (structural) | Add composable behavior versus control access to a collaborator. Discuss delegation, wrapper order, transparency, and the limits of substitutability. | Compose notification decorators and implement an access-checking proxy. Test wrapper order and allowed/denied access. |
| **8** | **Bridge** (structural) | Separate two independently changing dimensions. Compare Bridge with Adapter and Strategy; discuss why similar diagrams do not imply the same intent. | Combine report types and output channels without creating a subclass for every possible combination. |
| **9** | **Object trees and traversal: Composite + Iterator** (structural / behavioral) | Represent part–whole trees and traverse collections without exposing their representation. Revisit recursion, generics, and Java's `Iterable` and `Iterator` contracts. | Model a hierarchy of course modules and lessons, then implement and test an iterator with a defined traversal order. |
| **10** | **Object communication: Observer + Mediator** (behavioral) | Notify subscribers versus centralize coordination. Discuss subscription lifecycle, notification order, failure handling, and the risk of an oversized mediator. | Implement enrollment notifications and coordinate registration components through a mediator. Test unsubscribe behavior and coordination rules. |
| **11** | **Actions and undo: Command + Memento** (behavioral) | Represent requests as objects and separate invokers from receivers. Capture and restore state without exposing internals. Compare inverse operations with snapshot-based undo, including memory costs and irreversible side effects. | Implement editor commands and an undo history backed by mementos. Test multiple edits and restoration without exposing mutable snapshots. |
| **12** | **Lifecycle behavior: State** (behavioral) | Encapsulate behavior that changes with an object's state. Define legal transitions and who controls them. Contrast State's lifecycle-driven behavior with Strategy's interchangeable algorithms. | Model an assignment submission lifecycle with draft, submitted, and graded states. Test state-specific operations and invalid transitions. |
| **13** | **Request routing: Chain of Responsibility** (behavioral) | Pass a request through ordered handlers and define when processing stops. Discuss unhandled requests and configurable chains. Compare responsibility routing with Decorator's wrappers and Command's request objects. | Implement an approval chain in which each handler either handles a request or forwards it. Test handler order, escalation, and the unhandled case. |
| **14** | **Operations on object trees: Visitor + Interpreter** (behavioral) | Build on Composite's recursive structures. Use Visitor and double dispatch to add operations to a stable set of element types. Use Interpreter to represent and evaluate a small grammar. Compare adding operations with adding node types, and discuss the limits of a hand-built interpreter. | Represent a small arithmetic language as an expression tree and evaluate it with Interpreter. Add a Visitor for formatting expressions. Test nested expressions and discuss the changes needed for a new expression type. |

### Why this sequence?

Strategy and Template Method establish composition and inheritance before students use them in factories and other patterns. Weeks 3–5 explore object creation, copying, lifetime, and sharing. Weeks 6–9 develop interface boundaries, delegation, and recursive structures. Weeks 10–13 focus on communication, actions, lifecycle behavior, and request routing. Week 14 uses the object-tree foundation to teach Visitor and Interpreter together.

Pairings highlight either a useful contrast, such as Adapter versus Facade, or a natural collaboration, such as Command with Memento. Every week includes pattern instruction and a Java lab; refactoring and design comparisons are embedded in those lessons.

### Week 1 foundation checklist

Week 1 establishes the vocabulary used throughout the course. SOLID is introduced through small examples and reinforced in later weeks rather than treated as mastered in a single session.

- **Java essentials:** JDK, compiler and JVM; compiling and running a program; classes, constructors, methods, packages, and access modifiers; interfaces and abstract classes.
- **OOP essentials:** objects and responsibilities, encapsulation, abstraction, inheritance, and polymorphism; interface versus implementation; association, composition, and delegation.
- **Design essentials:** high cohesion, low coupling, separation of concerns, programming to interfaces, favoring composition over inheritance, and encapsulating what varies.
- **SOLID:** Single Responsibility, Open/Closed, Liskov Substitution, Interface Segregation, and Dependency Inversion. Distinguish dependency inversion from dependency injection, using constructor injection as a simple technique.
- **Practical restraint:** DRY (Don't Repeat Yourself), KISS (Keep It Simple), and YAGNI (You Aren't Gonna Need It). Avoid speculative abstractions and pattern use for its own sake.
- **Reading and checking designs:** basic UML relationships, behavior-focused unit tests, and a first Git commit.
- **Starter pattern:** Strategy, demonstrated with a small interface, two implementations, and a client that receives its strategy through a constructor.

## Pattern coverage

The sequence groups patterns by learning dependencies and useful comparisons, rather than teaching an entire category at once. Every GoF pattern appears below; repeated classroom discussion does not count as a new pattern.

| Category | Patterns and teaching weeks |
| --- | --- |
| **Creational — 5** | Factory Method (3), Abstract Factory (3), Builder (4), Prototype (4), Singleton (5) |
| **Structural — 7** | Flyweight (5), Adapter (6), Facade (6), Decorator (7), Proxy (7), Bridge (8), Composite (9) |
| **Behavioral — 11** | Strategy (1), Template Method (2), Iterator (9), Observer (10), Mediator (10), Command (11), Memento (11), State (12), Chain of Responsibility (13), Visitor (14), Interpreter (14) |

Numbers in parentheses indicate the week each pattern is first taught. All 23 patterns are covered during the course.

## Weekly practice

Weekly exercises should include runnable Java code, focused tests, and a short explanation of the problem, the chosen design, and its trade-offs. Students should be able to explain the roles in their own implementation without relying on pattern names alone.

Labs reuse familiar domains, such as course registration and document processing, so students can focus on the design problem. Each lesson includes a small change request or design comparison to show when the pattern helps and when a simpler solution is sufficient.

## Course resources

The [TSU Design Patterns GitHub organization](https://github.com/tsu-design-patterns) is the home for course materials and code, and this profile contains the course agenda. Lessons with guided labs and runnable Java examples are published on the course website, [tsu-design-patterns.github.io](https://tsu-design-patterns.github.io), as they become available. Their source is in the [website repository](https://github.com/tsu-design-patterns/tsu-design-patterns.github.io).
