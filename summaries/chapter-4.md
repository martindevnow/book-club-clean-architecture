## Chapter 4: Structured Programming

Edsger Wybe Dijkstra thought programming could be made easier by using proven mathematical concepts (proofs) and tie them together with code. His first step was to write basic proofs of simple algorithms in code. Throughout his experiments he realized _goto_ statements prevented modules from being recursively reduced. However, some patterns of _goto_ proved useful - these corresponded to control flow structures like _if_, _then_, _else_ etc. He published his findings, to much controversy, but ultimately his arguments were accepted by the greater community.

Structured programming allows modules to be recursively reduced. A large-scale problem can be reduced to high-level modules. High-level functions can be reduced to lower-level functions, and so on. Each of the decomposed functions can be represented using control flow concepts. (Eg. Modules -> components -> smaller components -> etc.)

In Dijkstra's ideal world problems should be reduced to tiny provable functions. However, the programming community didn't see value in proving every single function correct. Few believe formal proofs are an appropriate way to produce high-quality software. It makes more sense to apply the scientific method - _proving statements false_.

_Dijkstra: "Testing shows the presence, **not** the absence of bugs."_ All tests can do is allow us to say a program is correct enough for our purposes.

Through structured programming, we recursively decompose a program into a small set of provable functions. Then, we test if these functions are incorrect. If our tests cannot prove our functions are broken, then we can say they are good enough.
