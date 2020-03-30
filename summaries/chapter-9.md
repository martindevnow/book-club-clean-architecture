## Chapter 9: LSP: The Liskov Substitution Principal

The goal of LSP is to follow the substitution propert, defined roughly as:

> If a Program (`P`) that uses a Class (`A1`) can have `A1` substituted for another class (`A2`) without changing the behaviour of `P`, then `A2` is a subtype of `A1`.

### Guiding the Use of Inheritance

When a Class depends on a method defined on an Interface, any implementation of that Interface can be used by said Class.

### Square Rectangle Problem

An infamous example is if a `User` class depends on a `Rectangle` class, one might assume that a `Square` is a subtype of a `Rectangle`. However, it is likely that the class signatures are different given that a `Rectangle` can manipulate length and width independantly, where as the `Square` would likely have a different implementation. 

Therefore, in the `User` class, any method that depends on the `Rectangle` class could not easily be substituted for a `Square` without changing the logic of manipulating the *shape*.

> Since the behaviour of the `User` depends on the type it uses, those types are no substitutable

### LSP and Architecture

In early years, LSP was seen as a way to guide the use of inheritance. Over the years, it morphed to advise on software design that pertains to interfaces and implementations. In this case, Interfaces can be much more than just a class interface in code. It can also be applied to things like REST services.

### Example LSP Violation

If your app relies on a REST API that conforms to a contract you've provided, if another vendor were to deploy an API that did not adhere to that same contract, those two would not conform to LSP and are not substitutable. The program that depends on the REST API would need to add in additional logic to adapt to the broken contract, thus also breaking other SOLID principals.

### Conclusion

> The LST can, and should, be extended to the level of architecture. A simple violation of substitutability, can cause a system's architecture to be polluted with a significant amount of extra mechanisms.