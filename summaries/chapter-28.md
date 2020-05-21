# Chapter 28: The Test Boundary

> The tests are part of the system

## Tests as System Components

The type of test is irrelevant, they are architecturally equivalent.

Tests are the outermost circle in our software system. They depend on the system, but nothing in the system depends on them. Therefore, they follow the dependency rule.

They are also independently deployable (i.e. to test regions, but not prod).

> Tests are the most isolated system component. They are not necessary for system operation. Their role is to support development, not operation. They represent the model that all other system components should follow.

## Design for Testability

> Tests that are not well integrated into the design of the system tend to be fragile, and they make the system rigid and difficult to change.

> Tests that are strongly coupled to the system must change along with the system. Even the most trivial change to a system component can cause many coupled tests to break or require changes.

This is known as the _Fragile Tests Problem_.

> Don’t depend on volatile things, like GUIs. Test suites that operate the system through the GUI must be fragile. Therefore design the system, and the tests, so that business rules can be tested without using the GUI.

## The Testing API

The goal is to verify the business rules. The testing API should allow the tests to bypass security constraints and expensive resources (i.e. DB) and create testable states. This is a superset of the interactors and interface adapters.

This API should decouple the structure of the tests from the structure of the application.

### Structure Coupling

Having a test file for every production class and a set of tests for every method, this becomes deeply coupled to the system. This makes the tests fragile, and production code rigid.

The testing API should hide the structure of the app from the tests. This way, the production code can evolve without affecting the tests.

Strong structural coupling prevents the production code from being as general, and flexible, as it could be.

### Security

> The superpowers of the testing API could be dangerous if they were deployed in production systems. If this is a concern, then the testing API, and the dangerous parts of its implementation, should be kept in a separate, independently deployable component.

## Conclusion

Tests are a part of the system that must be designed well to provide stability and regression. Avoid tightly coupled, fragile tests.
