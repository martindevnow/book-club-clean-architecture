# Chapter 26: The `Main` Component

> In every system, there is at least one component that creates, coordinates, and oversees the others. I call this component `Main`.

## The Ultimate Detail

> The `Main` component is the ultimate detail—the lowest-level policy. It is the initial entry point of the system.

> It is in this `Main` component that dependencies should be injected by a Dependency Injection framework. Once they are injected into `Main`, `Main` should distribute those dependencies normally, without using the framework.

> The point is that `Main` is a dirty low-level module in the outermost circle of the clean architecture. It loads everything up for the high level system, and then hands control over to it.

## Conclusion

Kind of like bootstrapping. It is a plugin to the application, one that sets up the initial conditions and configurations, gathers all the outside resources, and then hands control over to the high-level policy of the application

> When you think about `Main` as a plugin component, sitting behind an architectural boundary, the problem of configuration becomes a lot easier to solve.
