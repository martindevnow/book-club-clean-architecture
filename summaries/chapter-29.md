# Chapter 29: Clean Embedded Architecture

A new definition of software vs firmware is discusses.

> “Although software does not wear out, firmware and hardware become obsolete, thereby requiring software modifications.”

Software is this thing that can have a long useful life, but firmware will become obsolete as hardware evolves. And so, the author notes that software can be destroyed from within by unmanaged dependencies on firmware and hardware.

It is posed that definitions of firmware which center around "software" which is stored in read-only software (in ROM, or flash memory) is obsolete. Instead, he argues that firmware is the software that is dependant on hardware. As such, non-embedded engineers also write firmware. This is demonstrated by SQL code is buried in the business rules.

He provides an example where a company's transition from a TDM (Time-Division Multiplexing) phone system to a VOIP phone system required constantly reviewing the legacy code to slowly extract the business rules as they were completely coupled to the old TDM system. This system became firmware.

## App-titude Test

Kent Beck describes three activities in building software 1.

1. “First make it work.” You are out of business if it doesn’t work.
2. “Then make it right.” Refactor the code so that you and others can understand it and evolve it as needs change or are better understood.
3. “Then make it fast.” Refactor the code for “needed” performance.

However, all to often developers focus too much on #1 and #3.

> Programmers who just concern themselves with getting their app to work are doing their products and employers a disservice.

A sample file is provided where the methods cross all types of different concerns from business rules, to reading IO, data persistence and poorly named methods.

> Virtually every bit of this code knows it is in a special microprocessor architecture,

The engineer, and the code, passed the App-titude test, but there is no way for this code
to have a long useful life unless the product never needs to be moved to a different
hardware environment. Therefore, it is not "Clean Embedded Architecture".

## The Target-hardware Bottleneck

It is noted that embedded systems are unique, but the software development is not _so_ unique as to negate the lessons in _Clean Architecture_. In fact, if the software is developed in a way that it can only be tested on the target-hardware, then the bottleneck will slow down development, as embedded systems have to deal with limited memory space, real-time constraints and deadlines, limited IO, unconventional user interfaces, and sensors and connections to the real world.

### A Clean Embedded Architecture is a Testable Embedded Architecture

A diagram is given showing Software on Firmware on Hardware. We know hardware will change over time. The line between hardware and the rest of the system is definite. However, trying to pass the _App-titude_ test could lead to hardware knowledge polluting the code.

Software and firmware should not intermingle as it will resist change. The line between software and firmware is not as well defined. It is the programmer's job to firm it up with the inclusion of a HAL (Hardware Abstraction Layer)

The HAL exists to serve the software that sits on top of it. The HAL provides a service, and it does not reveal to the software how it does it. For example, abstracting away the details of the persistence layer so the application is not concerned with how or where.

> You can see the HAL expressing services needed by the application. You can also see that layers may contain layers. It is more of a repeating fractal pattern than a limited set of predefined layers.

### Don't Reveal Hardware Details to the User of the HAL

A clean embedded architecture’s software is testable off the target hardware. A successful HAL facilitates this.

An example of a processor is given. What it boils down to is that device manufacturers may provide helper tool-chains, C header files, or other tools to easily interface with the hardware/peripherals. Though easy, using these throughout your code should be avoided. Take care of which files have knowledge of these tools/dependencies as your code will not compile without them. Think about how you would need to modify your code to move to a different processor (or hardware dependency).

> If you use a micro-controller like this, your firmware could isolate these low-level functions with some form of a processor abstraction layer (PAL).

It is also suggested that in cases where an embedded system ships with an RTOS (real-time operating system), the OS should be treated as a detail.

> A clean embedded architecture isolates software from the operating system, through an operating system abstraction layer (OSAL)

Depending on an OSAL instead of an OS directly means only having to rewrite the OSAL (to a defined interface and behaviour) instead of having to modify a bunch of complex existing code. This also helps provide test points so that the application code can be tested off-target and off-OS.

> A successful OSAL provides that seam or set of substitution points that facilitate off-target testing.

### Programming to Interfaces and Substitutability

Software > (OSAL) > OS > (HAL) > Firmware > > Hardware

> The idea of a layered architecture is built on the idea of programming to interfaces. When one module interacts with another though an interface, you can substitute one service provider for another.

In your header file, don’t clutter the interface header files with data structures, constants, and typedefs that are needed by only the implementation. Limit header file contents to function declarations as well as the constants and struct names that are needed by the function.

A clean embedded architecture is testable within the layers because modules interact through interfaces. Each interface provides that seam or substitution point that facilitates off-target testing.

### DRY Conditional Compilation Directives

Spreading out conditional logic to modify the behaviour depending on the hardware the software is being deployed to is an anti-pattern and violates DRY (Don't Repeat Yourself). Instead, an HAL would provide a set of interfaces, instead of using conditional compilation.

## Conclusion

> Letting all code become firmware is not good for your product’s long-term health. Being able to test only in the target hardware is not good for your product’s longterm health. A clean embedded architecture is good for your product’s long-term health.
