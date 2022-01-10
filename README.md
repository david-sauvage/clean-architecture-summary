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
