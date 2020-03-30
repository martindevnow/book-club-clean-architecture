## Chapter 7: SRP: The Single Responsibility Principal

This does not mean that a module should do only one thing. That is true of a function, but not what **SRP** is.

> A module should have one, and only one, reason to change.

The stakeholders (users, etc..) are the reason to change. These people can be grouped by their reason for wanting the change and defined as _actors_.

> A module should be _responsible_ to one and only one, _actor_

### Sympton 1: Accidental Duplication

When two functions rely on the same dependency (function or module) and those two functions are responsible to different actors, the shared dependency could be modified at the request of either actor causing issues and errors for the other actor (who did not request any changes)

i.e.) an `Employee` class that has a function `regularHours()` that is used by both the Accounting team and the Operations team.

### Sympton 2: Merges

Merge conflicts are a code smell. Two different developers touching the same code causing merge conflicts is a risky event, one to be avoided.

> Separate code that supports different actors

### Solutions

Separate code into separate classes that rely only on the data itself. A facade pattern can be used to simplify instantiating and tracking the multitude of dependencies.

### Conclusion

SRP is about functions and classes, but reappears at higher levels as **Common Closure Principal** for components and **Axis of Change** responsible for the creation of architectural boundaries.
