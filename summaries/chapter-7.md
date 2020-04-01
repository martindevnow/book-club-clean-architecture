## Chapter 6: SRP - The Single Responsibility Principle

Each software module is responsible for one, and only one, actor - an actor being a single or a group of people (users, stakeholders, etc) that require a change. This is highly dependant on the social structure of the organization.

### Symptom 1: Accidental Duplication

An example that violates the SRP & results in issues is the below:

You have an `Employee` class in a payroll application that has 3 methods responsible to 3 actors:

- `calculatePay()` -> accounting department (CFO)
- `reportHours()` -> HR department (COO)
- `save()` -> database administrators (CTO)

Putting these 3 methods in the sample `Employee` class couples them and thus couples the actors, which can result in the actions of the actors conflicting with each other.

To illustrate one scenario, picture a function `getRegularHours()` that calculates non-overtime hours. Accounting decides that the way this should be calculated needs to change, but HR also depends on this calculation and is unaware of the changes being made. This results in incorrect data for HR and drastically affects the budget.

### Symptom 2: Merges

Another example of an issue that arises is the likelihood of merge problems.

Using the same `Employee` class example, if Accounting & HR both decide their team needs to make changes to something in the class, both teams concurrently make their changes and it's very likely their changes will collide.

We need to avoid multiple actors changing the same source file for different purposes.

### Solutions

There are many different solutions, each involves moving the functions into different classes.

The most obvious solution is that in addition to making each function a separate class, we also separate the data. The 3 classes will now share access to the segmented `EmployeeData`, which is a simple data structure with no methods. The 3 classes hold their own source code, and they do not know about each other.

To alleviate having to track 3 different classes, we can build on this solution by using a _Facade_ pattern.

An `EmployeeFacade` would contain very little code and is only responsible for instantiating and delegating to the classes.

If you are more comfortable keeping the most important business rules closer to the data, the most important method can be kept in the `Employee` class and instead use the class as the _Facade_ for the less important functions.
