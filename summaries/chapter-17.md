# Chapter 17: Boundaries: Drawing Lines

- Don't make pre-mature decisions:
  deciding to use React, or Angular before knowing what your building.
  Coupling a Design system to your Data Model
  Picking the services, before designing the dependencies for those services.

## A Couple of Sad Stories

- P) choosing the "Architecture" too soon - Designing the Shape for the solution before knowing what shape was actually needed:
  - Three independent servers that act as µServices (GUI, Middleware, Database) all fully dependent on each other.
- W) choosing an "Architecture" that was too ridged. (Domain Model)
  - Enforcing a set of Models on development that far exceeded the needs of the system.

## FitNesses

- Making the right decisions early
  - choosing to pick a light "Self serve" server like npm start rather that depending on what you EXPECT the enterprise server allows you to defer that deciosn till later
  - it also help you create a solution that end up being more flexible - IE: can run on both Nginx or Apache - or even Serverless will little effort

## Drawing Lines - and when to draw them

- Building a Component in isolation with very limited dependencies, allows you to iterate upstream
  - Building a GUI that's isolated from the Business rules, that isolated from the DB.
    The use of an Interface between components allows these to remain decoupled. (relying on Selectors in your components rather than direct access to Data/State)
    Keeping State separate from your Backend.
  - Not only does this allow you to adapt to different solutions, it makes testing simpler.

## Input and Output

- IO is irrelevant.

## Plugin Architecture

- These patterns of a standard interface between Components leads to a Plugin In architecture
  - ie, while the initial build had mySql in mind, because it wasn't implemented against specifically, Postgress could be supported with the simple addition of a Plugin that matches the Interface for your the agnostic Component.
    _Wordpress's success largely hinges on it's extremely powerful support for Plugins!_

## The Plugin Argument

- Completely separate entities can build simultaneously when using the Plugin Architecture Pattern.
- Lines of dependency are important considerations - Code that depends on other code is vulnerable to changes from that other system.
  - Code that is depended on, is not vulnerable.

## Conclusion

- First, Partition your software into Components.
  - Separate component into concerns
- Second, Arrange the code such that the dependencies between then only goes in one direction.
  **This is an application of the Dependency Inversion Principle and Stable Abstractions Principle.**
