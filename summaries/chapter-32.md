# Chapter 32: Frameworks are Details

Frameworks are not architectures.

## Framework Authors

The authors are trying to solve their problems, not yours. They don't know you. Frameworks are only useful in the overlap between their problems and yours.

## Asymmetric Marriage

Using the framework, especially in a way that tightly couples your application to it, is a one-way relationship. You are committed to the framework, but the framework author has no commitment to you. It is a one-directional marriage. You take on all the risk and burden.

## The Risks

Some potential risks include:

- Violation of dependency rule. If your entities or use cases depend on the framework, that violates this principle.
- Though it may expedite early development, you may find your application fighting against the framework as your application grows.
- Old features you rely on may become deprecated, or new useless features may be added, increasing bloat and maintenance requirements.
- A better fitting framework may come along, but you've already coupled with your existing framework, preventing migration.

## The Solution

> Don't marry the framework!

Treat the framework as a detail on one of the outer circles of the architecture. Do not depend on it.

> If the framework wants you to derive your business objects from its base classes, say no! Derive proxies instead, and keep those proxies in components that are plugins to your business rules.

## I Now Pronounce You ...

Some frameworks must be married, but it should still be a decision. Your application will be forever coupled to whatever framework you marry.

## Conclusion

> When faced with a framework, try not to marry it right away. See if there aren’t ways to date it for a while before you take the plunge. Keep the framework behind an architectural boundary if at all possible, for as long as possible.
