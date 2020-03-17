## Chapter 6: Functional Programming

Using a `for` or `while` loop, relies on a mutable variable that changes its value during the program's execution. No such mutable variable exists in the Clojure functional equivalent.

> Variables in functional languages do not vary.

### Immutability and Architecture

> All race conditions, deadlock conditions, and concurrent update problems are due to mutable variables

If you have infinite storage and infinite processor speed, this is practical. However, the reality is more nuanced requiring certain compromises.

### Segregation of Mutability

This is the practice of separating components into mutable and immutable. Using some kind of transactional memory to protect the mutable variables from concurrent updates and race conditions.

> \[It is\] wise to push as much processing as possible into the immutable components, and to drive as much code as possible out of those components that allow mutation.

### Event Sourcing

> \[Event Sourcing\] is a strategy wherein we store the transactions, but not the state. When state is required, we simply apply all the transactions from the beginning of time.

Short cuts can be taken like nightly computations of state.

This is CR not CRUD. Removing updates and deletes also eliminates concurrent update issues. Given enough storage and processing power, we can make our applications entirely immutable, and thus entirely functional. This is how GIT source control works.

## Conclusion

> **Structured Programming** is discipline imposed upon direct transfer of control
> **Object-oriented Programming** is discipline imposed upon indirect transfer of control
> **Functional Programming** is discipline imposed upon variable assignment.

Each takes something away from the programmer. They define what not to do.

Rules of software have not changed. Software is composed of sequence, selection, iteration and indirection.
