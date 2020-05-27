# Chapter 27: Services: Great and Small

Microservices are popular as of late because of some partially true beliefs about them:

1. they are strongly decoupled from each other
2. they support independence of development and deployment

## Service Architecture?

Services in themselves are not architecture, as architecture is defined by boundaries \_between high-level policy and low-level detail. Services separating application behaviours are expensive function calls. Function calls that specifically cross architectural boundaries while respecting the Dependency Rule are architecturally significant.

## Service Benefits?

### The Decoupling Fallacy

Though they may not share code, or local variables, they can be coupled by shared processes, resources, network, or more importantly, the data they share. If adding a new field to a data record requires changing multiple services and they must interpret the data the same way, then those services are indirectly coupled to each other.

As for the well defined interface, it is no less well defined than a function interface.

### The Falacy of Independent Development and Deployment

It is believed that the _Service Architecture_ is scalable, but it has been seen with the monolithic app being scalable. As a service architecture scales to dozens and dozens of teams, we see the _Decoupling Falacy_ kick in an we see that independent development and deployment are not always possible, depending on the coupling of the data.

## The Kitty Problem

The author goes on to explain an scenario where a taxi company divides services by application feature. (taxi ui, finder, selector, dispatcher). He then points out that every one of these services would need to be changed to support a feature of delivering kittens and some customizations to the use-cases. (Drivers who cannot take kittens, customers who cannot ride in a car that had a kitten, etc)

> This is the problem with cross-cutting concerns.

## Objects to the **Rescue**

> Careful consideration of the SOLID design principles would have prompted us to create a set of classes that could be polymorphically extended to handle new features.

> Much of the logic of the original services is preserved within the base classes of the object model. However, that portion of the logic that was specific to rides has been extracted into a Rides component. The new feature for kittens has been placed into a Kittens component. These two components override the abstract base classes in the original components using a pattern such as Template Method or Strategy.

## Component-Based Services

Using SOLID principles we can apply them to services, such that new components can be added without changing the existing components within the service. THus, adding new features conforms to the OCP (Open Closed Principle).

## Cross-Cutting Concerns

Architectural boundaries run through services, not between them. Dealing with these cross-cutting concerns, services must be designed with internal component architectures that follow the Dependency Rule. The components withing these services will define the architectural boundaries.

## Conclusion

Services are useful for scalability and develop-ability, but not always architecturally significant.

> The architecture of a system is defined by the boundaries drawn within that system, and by the dependencies that cross those boundaries. That architecture is not defined by the physical mechanisms by which elements communicate and execute.

A service might be a single component, completely surrounded by an architectural boundary or, a service might be composed of several components separated by architectural boundaries.
