# Chapter 19: Policy and Level

> Software systems are statements of policy; a detailed description of the policy by which inputs are transformed into outputs.

These statements can be broken down into smaller statements of policy around business rules, report formatting or input validation.

Software architecture is carefully separating those policies and grouping them based on the ways that they change. (Think SRP [Single Responsibility Principle] or CCP [Common Closure Principle])

Architecture is forming these grouped components into an acyclic graph, outlining the dependencies between them directing the flow of dependencies from low-level to high-level.

## Level

> A strict definition of “level” is “the distance from the inputs and outputs.” The policies that manage input and output are the lowest-level policies in the system.

## Conclusion

Discussion around policies incorporates SRP, OCP, CCP, DIP, and SDP (Stable Dependency Principle)
