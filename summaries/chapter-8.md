## Chapter 8: The Open-Closed Principal

> A software artifact should be open for extension, but closed for modification.

### Thought Experiment

Financial data presented on a web page must now be printable to black and white printer paper.

In the situation where the `Web View Layer` is a module that depends on the `financial data`, we can easily build a new module for the `Printer View Layer` responsible to a new actor. This utilizes Dependecy Inversion (covered later) to allow us to decouple the data from it's dependencies.

The calculation of the data and the presentation of the data are two different responsabilities.

!! Insert Image !!

> An arrow pointing from class A to class B means that the source code of class A mentions the name of class B, but class B mentions nothing about class A.
> If component A should be protected from changes in Component B, then component B should depend on component A.

> Changes in the "Views" should not impact the "Presenter" just as changes in the "Presenter" should not impact the "Controller" and changes in the "Controller" should not impact the "Interactor".
> In this example, the **Interactor** is our _Business Logic_ and it should be most insulated from changes in the rest of the system.

> Higher level components in this hierarchy are protected from the changes made to lower-level components.

### Directional Control

Interfaces are inserted to ensure dependencies are pointed in the right direction.

### Information Hiding

The interface between the controller and the Interactor are designed to protect the Controller from changes in the Interactor, and prevent a transitive dependency on the `FinancialEntities` as this is a violation of the general principal that software entities should not depend on things they don't directly use.

### Conclusion

OCP's goal is to make the system easy to extend without incurring a high impact of change, by:

- partitioning the system into components
- arranging the components into a dependecy hierarchy that protects higher-level components from changes in lower level components
