# Clean architecture Summary


## Disclaimer
This is a summary of the book ["Clean Architecture: A craftsman's guide to software structure and design"](https://www.goodreads.com/book/show/18043011-clean-architecture) by Robert C. Martin (https://twitter.com/unclebobmartin)
I hope it's not a copyright infringement. If it is, please contact me to remove this file from Github.

## Summary

**1) Design and architecture**

Design and architecture are the same things. Design is often associated with details while architecture is about hight level structure but they are all part of the same whole.
The goal of software architecture is to minimize the human resources required to build and maintain the required system.
The main enemy of good design is the overconfidence of developers that wants to go fast. They think that they can clean the mess later but the reality is that it won't be possible
It's important to take the quality of software seriously and from the start.

**2) Behavior and structure**

Developers need to ensure the software lies on those two things: behavior and structure.
Behavior is simply the sum of the features provided by the software while the structure is how easy it is to change some behavior.
A common mistake is to privilege the behavior over the structure. Keep in mind that software that can't be changed is useless, therefore, structure is always important.

**3) The three paradigms**

There are only 3 paradigms : 
 - Structured programming (Discipline on direct transfer of control; no goto instructions)
 - Object-oriented programming (Discipline on indirect transfer of control ; no function pointers)
 - Functional programming (Discipline upon assignment ; no assignment)

**4) Structured programming**

Structured programming offers makes us create falsifiable units of programming.
This is why we still want to decompose our code as much as possible.
Software is like science, driven by falsifiability, meaning that we have to create small testable units of code.

**5) Object-oriented programming**

Object-oriented programming may often be defined by encapsulation, inheritance, and polymorphism.
Those three things were already doable with some trick in non-object-oriented languages.
Object-Oriented made them simpler. It also gives the ability, through polymorphism, to have control over source code dependency to make high-level modules independent from low-level modules.

**6) Functional programming**

The main benefit of functional programming is immutability. Immutability solves problems we can face in concurrency.
As seen before the three paradigms remove something from us. What we learned over the few decades of programming is what not to do and those rules haven't changed since Turing.

**7) Single responsibility principle**

A module should be responsible to one, and only one, actor.

**8) Open closed principle**

A software artifact should be open for extension but closed for modification
To achieve this principle, we need to arrange our components into a dependency hierarchy that protects high-level components from changes in the lower-level components.

**9) The Liskov substitution principle**

The Liskov substitution principle was created to guide the use of inheritance.
It is stated as follows: If for each object o1 of type S there is an object o2 of type T such that for all programs P defined in terms of T, the behavior of P is unchanged when o1 is substituted for o2 then S is a subtype of T

**10) The interface segregation principle**

Avoid depending on something that carries things you don't care about.

**11) The dependency inversion principle**

Try to depend only mostly on stable dependencies. Most of the time it will be an abstraction since it's easier for them to be stable.

The 5 previous principles are named the SOLID principles.

**12) Components**

It used to be difficult to use function libraries when writing our program. Today it's easy and components plugin architecture should be the default.

**13) Component cohesion**

The Reuse/Release equivalence principle: group for reuses
The common closure principle: group for maintenance
The common reuse principle: split to avoid unneeded releases

Those three principles will fight each other and it is the architect's job to choose which one the project needs more in its current state. This can change over time.

**14) Component coupling**

You should seek for non-cyclic dependency graph.
The direction of your dependency should be toward stable dependencies.
Components should be as abstract as they are stable

**15) What is architecture?**

Development, deployment, operation, maintenance. Those are the 4 aspects of software development.
We need to make those 4 aspects as easy as possible to have useful software.
A good architect will keep options open, meaning that he'll delay the details decision for as long as possible.

**16) Independence**

About decoupling:
- You can decouple by layers (UI, Business rules, database) or by uses cases
- On a larger scale, you can decouple at the source level, or deployment level, or service level

**17) Boundaries: Drawing lines**

The single responsibility principle will help you draw boundaries between components.
Some of those components are core business, others are plugins that are necessary but not directly related to core business.

**18) Boundary anatomy**

Boundaries in a system are often a mix of local chatty ones and others that are concerned with latency

**19) Policy and level**

A software is a set of policy. The level of a policy is the distance from the inputs and outputs. The farthest it is, the higher its level is.
High level policy tend to change less often than low level ones. Separate those policies and make the dependencies point toward the high level ones reduce the impact of change.

**20) Business rules**

Business rules are the core functionality of the system, they save or make money. They should be the most independent and reusable in the system

**21) Screaming architecture**

Your architecture should show what the system is about, not the framework it's using. The frameworks are only details.

**22) The clean architecture**

Framework -> Inteface adapters -> Application business rules -> Enterprise Business rules.
As seen previously, the entities are the inner circle, then the uses cases then the controllers then the UI, Database etc...
Only data will cross boundaries. And to do so, you should use simple data transfer objects. Don't cheat by using database rows or something like this that would violates the dependency rule.

**23) Presenters and humble objects**

Humble objects are often found at architectural boundaries. Those boundaries will involve a data structure and will divide something hard to test to something easy to test.
This pattern increase testability.
Example of humble projects : The view in MVP pattern or ORMs

**24) Partial boundaries**

Sometimes a boundary is expansive and we are not sure it is necessary. The architect may want to implement a partial boundaries in order to keep the option open.
You can either implement it without separating both part into two different components, creating one dimensional boundaries or use the facade pattern.
Keep in mind that over time, those partial boundaries may be degraded.

**25) Layers and boundaries**

Boundaries exists everywhere. Architects must recognize when they are needed. Despite the YAGNI principle that says we should not anticipate since the cost of adding a boundary is risky and costly. Nonetheless, we do not have to decide at the start of the project, we have to watch how the program evolve and look for friction and finally weight the cost of implementing the boundary and the cost of ignoring it.

**26) The main component**

The main component is the lowest level policy. It's the entry point, it creates everything then hand control over the high level policies.
See it as a plugin that sets initial conditions, doing so will make the problem of configuration much easier.

**27) Services: Great and small**

Services allows scalability and develop-ability but are not architecturally significant. The architecture is drawn by the boundaries of the system. 
Decoupling, independent development and deployment are fallacies when facing cross cutting concerns.
A service can be surrounded by architectural boundary or composed of several components separated by such boundaries.

**28) The test boundary**

Tests are part of the system. You have to design for testability or you will end up with a fragile and difficult to maintain test suite.
For example, it's a bad idea to test your business rules through UI. When you'll change your UI, all the test will fail, that makes your system hard to change.

**29) Clean embedded architecture**

Software should not be dependent on hardware or OS. Hardware and OS will evolve and if your software is tied to it, it will evolve poorly.
An abstraction layer is always needed when communicating with either one of them. That makes your software easier to maintain and to port to other systems.

**30) The database is a detail**

The data model is architecturally significant while the system that allows us to access it is not. Databases are only a detail.

**31) The web is a detail**

The GUI is a detail and the web is a GUI, therefore the web is a detail. As an architect, we need to keep it behind boundaries.
The interaction between a browser and the app is chatty and it needs to be abstracted to protect the business logic.

**32) Frameworks are details**

Using a framework is an asymmetrical marriage. You are linked to it without the authors of this framework being linked to you.
Try not to tie the core of your software with the frameworks you use.

**33) Case study**

The case study divides the components in two ways: by actors respecting the principle of single responsibility and by the Dependency rule. 
It separates components that change for different reasons and at different speeds. Thus structured, the project can be deployed in the most appropriate way.
