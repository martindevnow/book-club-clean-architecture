Chapter 14

Component Coupling

The forces that impinge upon architecture are technical, political and volatile.

The Acyclic Dependencies Principle
Allow no cycles in the component dependency graph

Morning After Syndrome - when something that you checked in last night no longer works. On smaller teams this is not an issue, however in larger teams it can be harder to manage a build as everyone keeps changing their code to make the build work with the changes that someone before them did. Two solutions have evolved to fix this problem :
The weekly build
The acyclic dependencies principle

The Weekly Build

The weekly build was common in medium to large sized projects. All developers ignored each other for the first four days of the week and on Friday they integrated everything together. Paying a large amount of penalty to do so. As the project grows it becomes much harder to finish the integration on Friday and the integration burden overflows until saturday. This convinces the developers to start to integrate sooner and sooner till the start of integration is earlier in the week.

As the cycle of integration versus integration decreases, so does the efficiency of the team and is frustrating for managers. Integration continues to grow with project size. With the scenario eventually leading to a crisis. To maintain efficiency, the build cycles are continuously lengthened. Lengthening of a build increases the project risk. Integration and testing are harder to do and the team loses the benefit of rapid feedback.

Eliminating Dependency Cycles

Partition the development environment into releasable components the components become units of worries that can be the responsibility of a single developer or a team of developers. When a developer has a component working, they release it for use to other developers . They give it a release number and move into a directory for other teams to use, they can continue to modify the item in their own private areas while everyone else uses the released versions.

As new releases become available, teams can decide whether to use this new component or if they decide not to, they can continue to use the old version. No team is at the mercy of the other team and changes that are made to a component do not need to affect the other team. Integration happens in small increments and this eliminates the problem where the developers were coming together to integrate everything that they were doing at regular intervals.

Directed Acyclic Graph
When it is impossible to follow the relationship between dependencies, and the structure has no cycles, this is a directed acyclic graph (DAG)

The Effect Of A Cycle In The Component Depandancy Graph

Cycles in a dependency graph make it difficult for you to work out the order that is needed to build components and this can cause some really bad problems

Breaking The Cycle

It easy to break the cycle and reinstate a dependency graph such as DAG, there are two primary mechanisms for doing so:

Apply the Dependency Inversion Principle
Creating an interface depends on into a new component.

The Jitters

As the application grows, the component structure jitters and grows. The dependency structure must always be monitored for cycles. When the cycles occur, these cycles myst be broken some how. This can mean making new components which can cause the dependency structure to grow,

Top Down Design

The component structure can not be designed from the top down. It evolves as the system grows and changes.

Component dependency diagrams are a map to the buildability and maintenance of the application. This is why they are not designed a the beginning of a project . As the project grows, there is a greater need to manage the dependencies so that the project is developed without the “morning after” syndrome. We start paying attention to the SRPand the CCP and we colocate the changes that are likely to change together.

One of the overriding principles with the depencancy structure is teh isolation of volatility. Cosmetic changes to the GUI should not have an impact on our business rules . Componnet dependency graph is created and molded by architects to protect the stable nad high value components from volatile components.

As the application grows, we become more concerned with creating reusable components. CRP begins to influence the composition of the components, Finally as cycles begin to appear, the ADP is applied and the component dependency graph jitters and grows

If we tried to design the component dependency structure before we designed the classes, we would fail really badly. We would be unaware about common closure and any reusable components that produce dependency cycles. The component dependency structure grows and evolves with the logical design of the system.

The Stable Dependency Principle

Designs can not be completely static. Some volatilatility is necessary if the design is to be maintained.By conforming to the common closure principle, we create components that are sensitive to certain types of changes and immune to others.

Any component that is expected to be volatile should not be depended on by a component that is difficult to change,

The perversity of the software that you have designed to be easy to change can be made difficult to change by someone else who has a dependency on it . Conforming to the Stable Dependencies Principle we ensure that the modules that are intended to be easy to change are not dependent on on modules that are harder to change.
