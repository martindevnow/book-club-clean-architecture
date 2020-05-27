# Chapter 3: Paradigm Overview

- Structured Programming: Imposes discipline on direct transfer of control. "Unrestrained jumps" such as _goto_ statements are harmful to program structure. Better to use flow control constructs like _if_, _then_, _else_ and _do_, _while_, _until_.

- Object-Oriented Programming (polymorphism): Imposes discipline on in-direct transfer of control. Functions become class contructors, local variables become instance variables, nested functions become methods.

- Functional Programming: Imposes discipline on assignment. The values of symbols do not change, they are _immutable_. Functional languages let coders modify variable values under specific circumstances.

The 3 paradigms **remove** capabilities from the coder. None of them add new capabilities. They tell us what **not** to do. Together, the paradigms remove `goto`, function pointers and assignment. There is nothing left to take away so it's likely these will be the only negative paradigms seen.

We use the 3 paradigms to solve the 3 concerns of architecture.

- Polymorphism (Objected-Oriented Programming) to cross architectural boundaries -> Function
- Functional Programming to enforce rules on how we store and access data -> Data Management
- Structured Programming as the algorithmic foundation of our modules -> Separation of Components
