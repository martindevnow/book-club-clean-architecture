## Chapter 5: Object-Oriented Programming

What is it? "A way to model the world" or "The combination of data and function" are poor descriptors.

_"Encapsulation, inheritance, and polymorphism"_

### Encapsulation

Not unique to OO. Can be done with C. Implementation details can be hidden from consumers. C++ broke this perfect encapsulation. The compiler provides protection, but the consumer can see the implementation details. `private`, `public` and `protected` were added as a hack to keep the member variables visible to the compiler, but restrict access to the consumer.

Java and C# removed header/implementation split weakening encapsulation. It is impossible to separate the declaration and definition of a class in these languages.

Instead, OO depends on programmers being well-behaved enough to not circumvent encapsulated data.

### Inheritance

Inheritance is simply the redeclaration of a group of variables and functions within an enclosing scope. This was possible without OO languages. OO did however make it significantly more convenient.

### Polymorphism

Polymorphism is an application of pointers to functions. OO made this much safer and more convenient. Explicitly using pointers to make functions polymorphic can be dangerous when any programmer forgets to follow convention.

OO eliminates these conventions. OO imposes discipline on indirect transfer of control.

#### Power of Polymorphism

Build a program that accept plugins that meet a specific specification but doesn't care about implementation details. Programs should be device independent. OO allows the plugin architecture to be used anywhere, for anything.

#### Dependency Inversion

Calling high level functions required that the function be imported where it is being called. (Like a `require` in JS or `import` in ES6+)
Leveraging polymorphism and OO allows any source code dependency to be inverted. An Interface is a tool used during programming, but is absent once compiled but enable reliable inversion of control. OO thus allows absolute control over the direction of all source code dependencies in the system.

This means the UI and Database can be plugins to the business rules. It means that the business rules never mentions the UI or the database. They can be deployed separately and independently.

> OO is the ability, through polymorphism, to gain absolute control over every source code dependency in the system.
