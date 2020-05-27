# Chapter 11: DIP: The Dependency Inversion Principle

The Dependency Inversion Principle (DIP) tells us that the most flexible systems are those in which source code dependencies refer only to abstractions, not to concretions.

In a statically typed language as in dynamically typed languages, source code dependencies should not refer to concrete modules.

The author says that treating this idea as a rule is unrealistic. In a real-world, software systems must depend on many concrete facilities. As an example, the Java's class `String` is concrete and we must not force to be abstract.

Also is important to mention that the `String` class is very stable, and changes are very rare and tightly controlled.

The author highlights that it is the volatile concrete elements of the system that we want to avoid depending on.

## Stable Abstractions

Every change in an abstract interface corresponds to a change in its concrete implementations. On the other hand, changes to concrete implementations do not always require changes to the interfaces they implement. Interfaces are less volatile than implementations.

We must aim to to reduce the volatility of interfaces, trying to find ways to add functionality to implementations without making changes to the interfaces. This is Software Design 101.

In summary, stable software architectures are those that avoid depending on volatile concretions, and that favor the use of stable abstract interfaces.

The coding practices for that are:

> Don’t refer to volatile concrete classes, refer to abstract interfaces instead;

> Don’t derive from volatile concrete classes;

> Don’t override concrete functions;

> Never mention the name of anything concrete and volatile.

## Factories

To exemplify the use of the Abstract Factory pattern to manage the dependency, observe the next figure, the `Application` uses the `ConcreteImpl` through the `Service` interface. However, the `Application` must somehow create instances of the `ConcreteImpl`. In other to do it without creating a source code dependency on the `ConcreteImpl`, the `Application` calls the `makeSvc` method of the `ServiceFactory` interface. This method is implemented by the `ServiceFactoryImpl` class, which derives from `ServiceFactory`. That implementation instantiates the `ConcreteImpl` and returns it as a `Service`.

<img width="487" alt="11-1" src="https://user-images.githubusercontent.com/16246749/78097391-2f18a400-73aa-11ea-9829-5d93c8079dd0.png">

> Note that the flow of control crosses the curved line in the opposite direction of the source code dependencies. The source code dependencies are inverted against the flow of control—which is why we refer to this principle as Dependency Inversion.

> OBS: The curved line divides the system into two components: one abstract and the other concrete. The abstract component contains all the high-level business rules of the application. The concrete component contains all the implementation details that those business rules manipulate.

## Concrete Components

DIP violations cannot be entirely removed, as we can see in the previous figure, but they can be gathered into a small number of concrete components and kept separate from the rest of the system.

Most systems will contain at least one such concrete component—often called `main`, the first started up function invoked by the OS.

## Conclusion

> The curved line in the last Figure will become the architectural boundaries in later chapters. The way the dependencies cross that curved line in one direction, and toward more abstract entities, will become a new rule that we will call the `Dependency Rule`.
