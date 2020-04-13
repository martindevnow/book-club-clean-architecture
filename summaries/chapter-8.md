## Chapter 8: OCP - The Open-Closed Principle

This principle states that to make software easy to change, it must allow for changes to be made by adding new code rather than changing existing code. If simple changes to the requirements results in massive changes to the software, the architecture of it is flawed.

### A Thought Experiment

Take for example a system that displays a financial report on a webpage, and stakeholders ask that a different printable report view must be made. Ideally, the amount of old code that needsd to change should be zero or the barest minimum, and only new code added.

We can help achieve this by following other design principles as well:

- We can separate things that change for different reasons (Single Responsibility Principle) - the calculation of the reported data and the presentation of the data into web & print forms.
- We organize the dependencies properly (Dependency Inversion Principle) - ensure that changes to one responsibility does not cause changes to the other, and that this organization ensures behaviour can be extended without undo modification.

If we partition the processes into classes, and separate them into components, we get for this example some components such as a `Controller`, `Presenters`, an `Interactor`, a `Database`, and web and PDF `Views`.

The flow of dependency between these components should be **unidirectional**, going from the least important to protect from change to the most important. To protect a component from changes, it should be the dependency for other components rather than depend on others.

In this case the most important component is the `Interactor` that contains the highest level policies & concepts. It will have the lesser components depend on it, and even lesser components depend on those, and so on until we get to the `Views` which have the lowest level concepts.

### Information Hiding

Software entities should not depend on things they don't generally use. We can have interfaces that serve the purpose of protecting entities from knowing too much about other ones. This can help further protect components from changes, and can be implemented to also protect lower concept components from changes to higher concept components.
