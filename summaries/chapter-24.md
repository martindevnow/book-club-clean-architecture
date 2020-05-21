# Chapter 24: Partial Boundaries

Setting up a boundary of two independently compilable and deployable components as described before can be expensive up front. In an even where you don't want to close yourself off to not doing it, you can establish a partial boundary.

## Skip The Last Step

One example is to do the work, but keep them together (compiled and deployed together). The same amount of development work/code is required, but no administration of multiple components, versioning, release management, etc. (Look pack at the FitNess example)

Although this can be a slippery slope as it makes it easier to cause coupling between them as they reside in the same component, possibly making it harder to separate them in the future.

## One-Dimensional Boundaries

Instead of having reciprocal boundary interfaces, a simpler structure that could hold it's place is a traditional _Strategy_ pattern os using a `ServiceBoundary` interface used by the client and implemented by `ServiceImpl` classes. This sets the stage for a proper architectural boundary, with necessary DIP in place.

This too can quickly degrade if not for discipline and diligence of developers and architects.

## Facades

By sacrificing the DIP, a `Facade` class which defers method calls to calls on services classes that the `Client` was not supposed to access. However, this creates a transitive dependency between the `Client` and the `Service` classes

It's easy to see how quickly this can fall apart.

## Conclusion

These are only three possible strategies for a partial architectural boundary, each with costs and benefits.

> It is one of the functions of an architect to decide where an architectural boundary might one day exist, and whether to fully or partially implement that boundary.
