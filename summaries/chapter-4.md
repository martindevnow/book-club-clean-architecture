## Chapter 4: Structured Programming

Edsger Wybe Dijkstra, born in 1930, became the first programmer for the "Mathematical Center of Amsterdam". He saw programming as more of an intellectual challenge than theoretical physics, and chose it as his career. Having started his career in the era of vacuum tubes, and punch cards, he made his great discoveries.

Being a mathematician, he set out to define programming structures as "proofs" that could be composed, but noticed that certain uses of `goto` statements prevented breaking down the code into modules. These uses were related to _selection and iteration_ control structures. Dijkstra proved _sequence, selection, and iteration_ through mathematical proofs. His proclamation that unwieldy use of `goto` statements was harmful was met with criticism and support. He eventually won out as proven by modern languages that prohibit unrestricted transfer of control.

### Functional Decomposition

This change allowed for modules to be recursively broken down into submodules, breaking down large-scale problems into high-level functions and then into lower and lower-level functions, all represented with restricted control structures. This idea caught on and spread throughout the 70s.

### No Formal Proofs

The dream of having formal proofs for every little function correct, slowly died, in favor of the _scientific method_.

### Science to the Rescue

The key difference is _They are falsifiable, but not provable_. Statements we cannot prove are false, we deem to be true for our purposes.

### Tests

> Testing shows the presence, not the absence of bugs.
> We show correctness by failing to prove incorrectness, despite our best efforts.

> Structured programming forces us to recursively decompose a program into a set of small provable functions, that can be tested to prove to be correct enough for our purposes buy failing to prove incorrectness.

Functional decomposition is one of our best practices. Software is like a science, driven by falsifiability.
