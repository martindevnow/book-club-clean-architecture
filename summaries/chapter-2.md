## Chapter 2: A Tale of Two Values

For stakeholders, they value the behaviour and the structure. As devs, we often focus on one to the detriment of the other.

- Behaviour: Help define functional specifications and requirements. Then build it. Many think this is where the line is. But that is incorrect.

- Architecture: Think “soft” where “ware” = product. Soft meant easy to change. Feature requests change over time and so must the code. The difficulty of making a change should be proportional only to the scope of the change, and not to the shape of the change.

Stakeholders see stream of change requests of approx. equal size. Devs see more and more puzzle pieces in a puzzle of ever growing complexity. The more your architecture prefers one shape over another, likely makes new features harder to fit into that structure. The goal is to be shape agnostic.

A broken system that is easy to change can be made to work. A working system that is difficult to change will eventually stop working. Beware of business managers that ask to prioritize functionality now over future flexibility, as if the cost to change the system increases, they will likely be furious.

Urgent and not important or important but not urgent. Behaviour is urgent, but not important. Architecture is important but not particularly urgent. Business managers are not equipped to evaluate the importance of architecture. This responsibility lies with the development team.

Each department fights for what they deem important. So should the development team fight for clean architecture. Remember that as developers, we are stakeholders. We have a stake in the software that we need to safeguard. Even more so for software architects (or solutions Architects). Their goal is to create and architecture that allows features and functions to be easily developed and easily modified and easily extended.

If architecture comes last, the system will become ever more costly to develop, and cause changes to be more and more difficult.
