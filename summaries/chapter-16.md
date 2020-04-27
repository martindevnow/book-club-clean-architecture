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

This balance is difficult when there are so many unknowns.

### Decoupling Layers

### Decoupling Use Cases

### Decoupling Mode

### Independent Develop-ability

### Independent Deployability

### Duplication

### Decoupling Modes (Again)

### Conclusion
