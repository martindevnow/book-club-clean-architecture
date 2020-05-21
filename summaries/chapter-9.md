# Chapter 9: LSP - The Liskov Substitution Principle

In order to build software systems from interchangeable parts, those parts must be able to be easily substituted for one another.

## Guiding the Use of Inheritance

An example is a `License` class use for a billing that has a `calcFee()` method, and 2 subtypes of Licenses for `PersonalLicense` and `BusinessLicense`. This conforms to the LSP because the behavior of the billing app does not depend on which of the subtypes are used.

## The Square/Rectangle Problem

An example of a violation of the LSP is when you try to consider a `Square` as a subtype of a `Rectangle`. The height and the width of the `Rectangle` are independently mutable (contains `setH()`, `setW()`) , when instead they must change together for the `Square` (only contains `setSide()`).

If a user believes they are communicating with a `Rectangle`, it can become confusing particularly if the code produces a `Square`. If we have assertions that depend on the sides being independently mutable, the assertions would fail. To fix tihs violation we need to add checks in this code to ensure we are not using a `Square`.

## Broadening to Interfaces and Implementations

Beyond just guiding inheritance, LSP has morphed into a broader principle that pertains to interfaces and implementations. More than before, we must create well-defined interfaces and focus on the substitutability of their implementations.

An example of another violation is an aggregator for many different taxi dispatch services that dispatches a chosen taxi via a restful service. The URI is captured in the driver database, and the chosen driver is dispatched using that URI.

The URI could look like:

```purplecab.com/driver/Bob
    /pickupAddress/24 Maple Street
    /pickupTime/153
    /destination/ORD
```

All the other dispatch services from the different companies must conform to the same REST interface, their fields being identical.

If a requirement came in that forced us to use different field names for a different company named Acme, we need to add special cases. Acme's dispatch request would have to be constructed with different rules from all the other ones, and we may end up implementing bad practices such as adding `if` statements to detect for the string `acme` throughout the code. This opens us up to erroneous results and security breaches. If more requirements come in that further complicate the situation, we need to add more mechanisms to insulate from more bugs.

Violating this principle can cause a system's architecture to be polluted with a significant amount of extra mechanisms.

## Conclusion

> The LSP can, and should, be extended to the level of architecture. A simple violation of substitutability, can cause a system's architecture to be polluted with a significant amount of extra mechanisms.
