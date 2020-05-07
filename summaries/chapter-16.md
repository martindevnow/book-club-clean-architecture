## Chapter 16: Independence

As we previously stated, a good architecture must support:

- The use cases and operation of the system.
- The maintenance of the system.
- The development of the system.
- The deployment of the system.

### Use Cases

This means the architecture should support the intent of the system.

> The use cases of that system will be plainly visible within the structure of that system. Developers will not have to hunt for behaviors, because those behaviors will be first-class elements visible at the top level of the system. Those elements will be classes or functions or modules that have prominent positions within the architecture

### Operation

Architecture plays a more substantial role here by enabling the throughput and response time expected from the system.

This could mean parallelization of processes or sharing of processing space and distributing the work across threads.

> This decision is one of the options that a good architect leaves open.

An architecture that maintains the proper isolation of its components, and does not assume the means of communication between those components, will be much easier to transition through the spectrum of threads, processes, and services as the operational needs of the system change over time.

### Development

> Any organization that designs a system will produce a design whose structure is a copy of the organization’s communication structure.

### Deployment

The goal: Immediate Deployment

> A good architecture does not rely on dozens of little configuration scripts and property file tweaks. It does not require manual creation of directories or files that must be arranged just so. A good architecture helps the system to be immediately deployable after build.

### Leaving Options Open

> A good architecture balances all of these concerns with a component structure that mutually satisfies them all.

This balance is difficult when there are so many unknowns; use cases, operational constraints, team structure, deployment requirements, etc.

> the goals we must meet are indistinct and inconstant

> A good architecture makes the system easy to change, in all the ways that it must change

### Decoupling Layers

> the architect can employ the Single Responsibility Principle and the Common Closure Principle to separate those things that change for different reasons, and to collect those things that change for the same reasons

For example, UI will change for a different reason than the business rules. Similarily, query language, schema, and the database have nothing to do with the business rules.

> The result is the system divided into decoupled horizontal layers

### Decoupling Use Cases

> Use cases are narrow vertical slices that cut through the horizontal layers of the system.

If you decouple the elements of the system that change for different reasons, then you can continue to add new use cases without interfering with old ones.

### Decoupling Mode

> If the different aspects of the use cases are separated, then those that must run at a high throughput are likely already separated from those that must run at a low throughput

> The decoupling that we did for the sake of the use cases also helps with operations. However, they must be independent services, which communicate over a network of some kind. (Micro-services / service-oriented architecture)

### Independent Develop-ability

> So long as the layers and use cases are decoupled, the architecture of the system will support the organization of the teams, irrespective of whether they are organized as feature teams, component teams, layer teams, or some other variation.

### Independent Deployability

> The decoupling of the use cases and layers also affords a high degree of flexibility in deployment.

### Duplication

**True Duplication**

> every change to one instance necessitates the same change to every duplicate of that instance

**False Duplication**

> change at different rates, and for different reasons

Care must be taken to avoid unifying cases of accidental or false duplication as separating them in the future would be a challenge

> Resist the temptation to commit the sin of knee-jerk elimination of duplication. Make sure the duplication is real.

**Example:**

Database data is similar to the UI data, but passing the DB record straight to the UI would be accidental duplication. A view model is low effort and insulates from different reasons to change each.

### Decoupling Modes (Again)

Use cases can be decoupled at the source code level, binary (deployment) level or execution unit (service) level.

- Source Level: We can control the dependencies between source code modules so that changes to one module do not force changes or recompilation of others

- Deployment Level: the decoupled components are partitioned into independently deployable, so that changes to the source code in one module do not force others to be rebuilt and redeployed. (i.e. sockets)

- Service Level: reduce the dependencies down to the level of data structures, and communicate solely through network packets such that every execution unit is entirely independent of source and binary changes to others

Which is best?

Hard to say. Needs change as the system and it's needs evolve. One solution, decouple at service level by default. This can be expensive and encourages _coarse-grained_ decoupling. Also, dealing with service boundaries where none are needed is a waste of effort, memory, and cycles.

Another approach, separate components at source code level initially, and can be pushed to decouple at deployment as development, deployment and operational issues increase. Gradually, this can shift woards services.

> A good architecture will allow a system to be born as a monolith, deployed in a single file, but then to grow into a set of independently deployable units, and then all the way to independent services and/or micro-services. Later, as things change, it should allow for reversing that progression and sliding all the way back down into a monolith.

> Good architecture protects the majority of the source code from those changes.

### Conclusion

> The decoupling mode of a system is one of those things that is likely to change with time, and a good architect foresees and appropriately facilitates those changes.
