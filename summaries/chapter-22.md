## Chapter 22: The Clean Architecture

There have been recent ideas of _Clean Architecture_ which share a common thread.

- Independant Frameworks
- Testable
- Independent of UI
- Independent of DB
- Independent of external agency

### The Dependency Rule

Entities > Use Cases > Controllers / Gateways / Presenters > DB / Web / UI etc

High level > > > Low Level

> **The Dependency Rule**
> Source code dependencies must point only inward, toward higher-level policies.

Nothing on the left can know about the parts on the right.

#### Entities

No operational change should impact Entities. They are least likely to change.

#### Use Cases

> We do not expect changes in this layer to affect the entities. We also do not expect this layer to be affected by changes to externalities such as the database, the UI, or any of the common frameworks.

Changes in the operation of the application will affect the use cases (and thus, this code)

#### Interface Adapters

The presenters, views, and controllers all belong in the interface adapters layer, converting data from use cases to the format most convenient for some external agency like a DB or the UI. This layer also transforms the inputs from externa agents into data structures convenient for the use cases and entities.

#### Frameworks and Drivers

> Generally you don’t write much code in this layer, other than glue code that communicates to the next circle inward. The frameworks and drivers layer is where all the details go. The web is a detail. The database is a detail.

#### Only Four Circles?

This is a schematic. There can be more, but the Dependency Rule applies.

> As you move inward, the level of abstraction and policy increases. The outermost circle consists of low-level concrete details.

#### Crossing Boundaries

In cases where inner circles must call outer circles, we can use dynamic polymorphism to create source code dependencies that oppose the flow of control, adhering to the Dependency Rule. The inner circle would call an interface at `use case output port`. No name from an outer circle can be referenced in an inner circle.

#### Which Data Crosses the Boundaries

Simple DTO, hashmap, arguments to a function call. It must be an isolated, simple data structure. We don't want to pass Entity objects or database rows. They cannot have a dependency in violation of the Dependency Rule.

> When we pass data across a boundary, it is always in the form that is most convenient for the inner circle.

### A Typical Scenario

[Discuss an Example]

### Conclusion

> By separating the software into layers and conforming to the Dependency Rule, you will create a system that is intrinsically testable, with all the benefits that implies. When any of the external parts of the system become obsolete, such as the database, or the web framework, you can replace those obsolete elements with a minimum of fuss.
