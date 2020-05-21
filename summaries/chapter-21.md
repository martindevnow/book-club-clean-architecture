# Chapter 21: Screaming Architecture

Looking at the blueprints to a building should make it readily apparent what you're looking at. The same should be true for software.

## The Theme of an Architecture

Software architectures are structures that support the use cases of the system. It should scream the use cases of the application.

> Frameworks are tools to be used, not architectures to be conformed to. If your architecture is based on frameworks, then it cannot be based on your use cases.

## The Purpose of an Architecture

The purpose of your house is to be livable. The architect ensures this criteria is met before decisions about materials.

> A good software architecture allows decisions about frameworks, databases, web servers, and other environmental issues and tools to be deferred and delayed. A good architecture emphasizes the use cases and decouples them from peripheral concerns.

## But What About the Web?

The web is IO.

> You should be able to deliver it as a console app, or a web app, or a thick client app, or even a web service app, without undue complication or change to the fundamental architecture.

## Frameworks Are Tools, Not Ways of Life

> Look at each framework with a jaded eye. View it skeptically. Yes, it might help, but at what cost? Think about how you can preserve the use-case emphasis of your architecture.

## Testable Architectures

If your architecture is about the use cases, you should be able to unit-test all of them without frameworks. No webserver, no database. Entities should have no dependencies on frameworks, or DBs.

## Conclusion

> Your architecture should tell readers about the system, not about the frameworks you used in your system.

M before VC
