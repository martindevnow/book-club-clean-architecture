# Chapter 27: Services: Great and Small

Microservices are popular as of late because of some partially true belifs about them:

1. they are strongly decoupled from eachother
2. they support independence of development and deployment

## Service Architecture?

Services in themselves are not architecture, as architecture is defined by boundaries \_between high-level policy and low-level detail. Services separating application behaviours are expensive function calls. Function calls that specifically cross architectureal boundaries while respecting the Dependency Rule are architecturally significant.

## Service Benefits?

### The Decoupling Fallacy

Though they may not share code, or local variables, they can be coupled by shared processes, resources, network, or more importantly, the data they share. If adding a new field to a data record requires changing multiple services and they must interpret the data the same way, then those services are indirectly coupled to eachother.

As for the well defined interface, it is no less well defined than a function interface.

### The Falacy of Independent Development and Deployment

It is believed that the _Service Architecture_ is scalable, but it has been seen with the monolithic app being scalable. As a service architecture scales to dozens and dozens of teams, we see the _Decoupling Falacy_ kick in an we see that independent development and deployment are not always possible, depending on the coupling of the data.

## The Kitty Problem

The author goes on to explain an scenario where a taxi company divides services by application feature. (taxi ui, finder, selector, dispatcher). He then points out that every one of these services would need to be changed to support a feature of delivering kittens and some customizations to the use-cases.

....

...
..

## Objects to the Rescoe

## Component-Based Services

## Cross-Cuttin Concerns

## Conclusion

Services are useful for scalability and develop-ability, but not always architecturally significant.

> The architecture of a system is defined by the boundaries drawn within that system, and by the dependencies that cross those boundaries. That architecture is not defined by the physical mechanisms by which elements communicate and execute.

A service might be a single component, completely surrounded by an architectural boundary or, a service might be composed of several components separated by architectural boundaries.
