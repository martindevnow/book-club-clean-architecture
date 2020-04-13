# Part 3: Design Principals

Good materials with bad strategy as well as bad materials with good strategy both lead to a mess. SOLID principals tell us how to group our code and how those groups of code should be interconnected.

SOLID is a set of design principles that can guide us on how our classes should be interconnected, classes being coupled groupings of functions and data structures, and also on how these functions and data structures should be arranged. They also help guide our software structures used within modules and components.

The goal is mid-level software structures that:

- tolerate change
- are easy to understand
- are the basis of components that can be used in many software systems

These principals are used at the module level.

SOILD dates back to the 80s and in 2004, the acronmy took form.

- **SRP** - Single Responsibility Principal

  > The module should have only one reason to change

- **OCP** - Open-Closed Principal

  > Open to extension, closed to modification

- **LSP** - Liskov Substitution Principal

  > Adherance to a contract to allow substitution of parts

- **ISP** - Interface Segregation Principal

  > Code to the interface, not the implementation

- **DIP** - Dependency Inversion Principal
  > Details should depend on the policies
