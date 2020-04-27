## Chapter 15: What is Architecture?

Software architects are the best programmers, and they continue to take programming tasks, while they also guide the rest of the team toward a design that maximizes productivity. They do this because they cannot do their jobs properly if they are not experiencing the problems that they are creating for the rest of the programmers.

The architecture of a software system is the shape given to that system by those who
build it:

- The division of that system into components
- The arrangement of those components
- The ways in which those components communicate with each other.

The purpose of that shape is to facilitate the development, deployment, operation, and maintenance of the software system contained within it.

> The strategy behind that facilitation is to leave as many options open as possible, for as long as possible.

The primary purpose of architecture is to support the life cycle of the system. Good architecture makes the system easy to understand, easy to develop, easy to maintain, and easy to deploy. The ultimate goal is to minimize the lifetime cost of the system and to maximize programmer productivity.

### Development

> The architecture of a system should make that system easy to develop, for the team(s) who develop it.

Small teams might not impose acrhitecture over fears of impediment of the superstructure. Systems developed by distributed teams will drive towards independant components, one per team.

> Such a component-per-team architecture is not likely to be the best architecture for deployment, operation, and maintenance of the system. Nevertheless, it is the architecture that a group of teams will gravitate toward if they are driven solely by development schedule.

### Deployment

> A goal of a software architecture, then, should be to make a system that can be easily deployed with a single action

Easy to develop doesn't mean easy to deploy. A Micro-service architecture may make the system very easy to develop since the component boundaries are very firm and the interfaces relatively stable. However, when it comes time to deploy the system, they may discover that the number of micro-services has become daunting; configuring the connections between them, and the timing of their initiation, may also turn out to be a huge source of errors.

> considering deployment issues early on, might lead to fewer services, a hybrid of services and in-process components, and a more integrated means of managing the interconnections.

### Operation

Hardware is cheap, and people are expensive. From an architecture POV, operation doesn't often take prioritiy.

> The cost equation leans more toward development, deployment, and maintenance.

Architecture should reveal operation. The architecture of the system should elevate the use cases, the features, and the required behaviors of the system to first-class entities that are visible landmarks for the developers. This simplifies the understanding of the system and, therefore, greatly aids in development and maintenance.

### Maintenance

Maintenance is the most costly.

A carefully thought-through architecture vastly mitigates the costs of debugging and the risk of patching. By separating the system into components, and isolating those components through stable interfaces, it is possible to illuminate the pathways for future features and greatly reduce the risk of inadvertent breakage.

### Keeping Options Open

Software has 2 types of value:

1. the behaviour
2. the structure (this is greater as it makes softeware _soft_)

The system then breaks down into 2 major elements:

1. policy (business logic and the value)
2. details (enable humans, other sustems and programmers to communicate with the policy without impacting the behaviour of the policy)

> The goal of the architect is to create a shape for the system that recognizes policy as the most essential element of the system while making the details irrelevant to that policy. This allows decisions about those details to be delayed and deferred.

i.e.)

- the driver for the persistence layer should be arbitrary
- the web server is irrelevant early on. The policy shouldn't care

> The longer you wait to make those decisions, the more information you have with which to make them properly.

The longer you leave options open, the more experiments you can run, the more things you can try, and the more information you will have when you reach the point at which those decisions can no longer be deferred.

> A good architect maximizes the number of decisions not made.

### Device Independence

Code that is specific or coupled to a specific device (input, output, etc) cannot easily be used with a different device.

See: the Open-Closed Principle

### Junk Mail

When printing templates for mail-adverts, they were easily able to test print to a local line printer. Once validated, they were "printed" to the magentic tape and brought offsite to be printed enmasse on cheaper technology. Device independence saves money.

### Physical Addressing

The move from physical addressing of locations on a HDD to using relative addressing via a converter allowed the data itself and the application to be more agnostic to the storage device. Moving the data became a less cumbersome task.

### Conclusion

> Good architects carefully separate details from policy, and then decouple the policy from the details so thoroughly that the policy has no knowledge of the details and does not depend on the details in any way. Good architects design the policy so that decisions about the details can be delayed and deferred for as long as possible.
