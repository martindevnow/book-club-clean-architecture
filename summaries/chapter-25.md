# Chapter 25: Layers and Boundaries

Some systems are as simple as UI, Rules and DB. Think about it...

## Hunt the Wumpus

Breaking down the UI into concepts to handle Language and Text Deliver and Data Storage. Between each of these is a boundary (and likely many more) where reciprocal boundary interfaces exist to allow the lower level details to be abstracted away from concerns of higher level components.

> The API defined by those Boundary interfaces is owned by the upstream component.

The variations are provided by polymorphic interfaces defined in the abstract API component and implemented by the concrete components that serve them. The game's rules being at the top, the highest level.

Input from the user flows through `TextDelivery` to `Language` to be interpreted, and up to `GameRules` while data from the `DataStorage` also flows up to the `GameRules`. Output then flows back to `Language` to be interpreted back to the user's language and to `TextDelivery` to be displayed.

> This organization effectively divides the flow of data into two streams.2 The stream on the left is concerned with communicating with the user, and the stream on the right is concerned with data persistence. Both streams meet at the top3 at GameRules, which is the ultimate processor of the data that goes through both streams.

## Crossing the Streams

There could be a third, `Network` Stream, also controlled by the `GameRules`. There could be more.

## Splitting the Streams

Steams don't always meet up at the same component. `GameRules` could easily be split to represent the complexity of the game. Imagine the policies that govern movement and those that govern player health and cost/benefit of events occurring in the game. The movement module could declare events to the higher policy such as `FellInHold` or `FoundFood`. The higher level policy could be responsible for the win/loss condition.

## Conclusion

What's the point of all this work?

> Architectural boundaries exist everywhere. We, as architects, must be careful to recognize when they are needed. We also have to be aware that such boundaries, when fully implemented, are expensive. At the same time, we have to recognize that when such boundaries are ignored, they are very expensive to add in later—even in the presence of comprehensive test-suites and refactoring discipline.

> The philosophy of YAGNI: “You aren’t going to need it.” There is wisdom in this message, since over-engineering is often much worse than under-engineering. On the other hand, when you discover that you truly do need an architectural boundary

> This is not a one-time decision. You don’t simply decide at the start of a project which boundaries to implement and which to ignore. Rather, you watch. You pay attention as the system evolves.

> You weigh the costs of implementing those boundaries versus the cost of ignoring them—and you review that decision frequently. Your goal is to implement the boundaries right at the inflection point where the cost of implementing becomes less than the cost of ignoring.
