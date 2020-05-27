# Chapter 20: Business Rules

There are different kinds of business rules; rules or procedures that make or save the company money.

A bank charging an interest rate `N%` on a loan is a business rule (A _Critical Business Rule_; one which must be automated) and it relies on data (_Critical Business Data_; which the automated system needs). These two are bound and called an **entity**.

## Entities

> An Entity is an object within our computer system that embodies a small set of critical business rules operating on Critical Business Data.

It has either the data, or easy access to it. It's interface has functions implementing the business rules. It becomes a class to implement a concept critical to the business.

> An Entity is business and _nothing else_.

It does not require OOP, it only requires you combine data and rules in a single and separate module.

## Use Cases

> Some business rules make or save money for the business by defining and constraining the way that an automated system operates. These rules would not be used in a manual environment, because they make sense only as part of an automated system.

i.e. Gathering critical user details in order to validate sufficient credit score before allowing the user to proceed is a _use case_.

> A use case is a description of the way that an automated system is used. It specifies the input to be provided by the user, the output to be returned to the user, and the processing steps involved in producing that output.

These are application-specific business rules as opposed to the _Critical Business Rules_ within the Entities

> Use cases contain the rules that specify how and when the Critical Business Rules within the Entities are invoked.

There is no mention of UI, only data interfaces.

> Use cases do not describe how the system appears to the user. Instead, they describe the application-specific rules that govern the interaction between the users and the Entities.

It is an object that has functions that implement the application's business rules with data from the input, output or entities.

Entities are higher level concepts than use cases. Therefore, entities have no knowledge of them making them easier to change than the entities. (Ref: DIP)

Use cases represent a specific application, close to the IO. Entities are generalizations in many applications, farther from the IO.

Use cases depend on entities, not the other way around.

## Request and Response Models

Use cases depend on IO data. However, they do not care how they get the IO data. They do not define the communication method and know nothing of SQL, HTML, etc..

These use cases have a unique request and response models (or interface or data structure). This lack of dependencies is critical as shared interfaces could cause unnecessary coupling. Also, referencing the entities of the use case in the request/response would violate SRP and CCP as entities and these models change for very different reasons.

## Conclusion

> The business rules should remain pristine, unsullied by baser concerns such as the user interface or database used. Ideally, the code that represents the business rules should be the heart of the system, with lesser concerns being plugged in to them. The business rules should be the most independent and reusable code in the system.
