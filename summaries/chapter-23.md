## Chapter 23: Presenters and Humble Objects

Presenters are a form of the Humble Object pattern. They help us identify architectural boundaries

### The Humber Object Pattern

> Split a module into two; testable, and hard-to-test (humble).

For example, UI is hard to unit test (humble). The behaviour can be tested. These are the views (humble) and the presenter respectively.

### Presenters and Views

The view should be as simple as possible with as little data as possible. The presenter is testable. It should take application data and format it for the presentation so that the view can simply displasy it. The presenter takes a `Date()` object and provides a formatted string to the view model, accessible by the view. Changing formatting (i.e. color font) should be a flag in the view model data. Every aspect of the UI should be represented in the View model. Nothing is left for the view to do but display the View model on screen. Thus the View is humble.

### Testing and Architecture

We know this is important and the _Humble Object Pattern_ is more evidence.

### Database Gateways

They sit on the boundary between use case interactors and the DB. They have polymorphic interface method for every call that can be performed. SQL cannot go into the use case layer, so we use gateway interfaces implemented by classes in the DB layer. They are humble objects. They simply run SQL. The interactors though are not humble, but testable (thanks to the interfaces) via mocks and stubs.

### Data Mappers

ORM (Object Relational Mapper) ought be named "data mappers" as they load data into data structures from relational database tables. ORMs exist in the DB layer

### Service Listeners

The Humble Object pattern can create a boundary here too by loading data into simple data structures (DTO) and pass it across the boundary to a module that formats the data and sends it to the service. Upon receiving external data back, it again formats the response into a simple DTO that can be used in the app, passed across the service boundary.

### Conclusion

> At each architectural boundary, we are likely to find the Humble Object pattern lurking somewhere nearby. The communication across that boundary will almost always involve some kind of simple data structure, and the boundary will frequently divide something that is hard to test from something that is easy to test. The use of this pattern at architectural boundaries vastly increases the testability of the entire system.
