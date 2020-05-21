# Chapter 6: Functional Programming

Variables in functional languages (Clojure) are immutable. Race conditions, deadlocks and concurrent update problems are due to mutable variables. All problems we face in applications with multiple threads and multiple processors require mutable variables. Pure immutability is not practical as it requires large amounts of storage and processor speed (infinite?). Immutability requires compromises.

## Segregation of Mutability

A common compromise is to separate the application into mutable and immutable components. Immutable components perform tasks in a purely functional way, without using mutable variables. Mutating state exposes components to concurrency problems, therefore it's common practice to use **transactional memory** to protect mutable variables. Transactional memory treats variables in memory like a database treats records on disk: through a _transaction (retry)-based scheme_.

Simple example: Clojure `atom` facility:

```
(def counter (atom 0)) ; initialize counter to 0
(swap! counter inc) ; safely increment counter
```

In this example, `atom` can only be mutated under conditions enforced by the `swap!` function. `swap!` takes two arguments, the `atom` to mutate and a function which mutates the `atom`. `swap!` uses a _compare and swap_ algorithm to prevent side effects:

- The value of `counter` is read and passed to `inc`
- When `inc` returns, the value of `counter` is locked
- Compare the returned value with the value initially passed to `inc`
- If the value is the same, the returned value of `inc` is stored in `counter` successfully and `counter` is unlocked
- If the value is different, `counter` is unlocked and the algorithm is retried

This is only suitable for simple applications and cannot guarentee immutability when there are many dependent variables.

## Event Sourcing

The more memory and processing power we have, the less we need mutable state. Consider a banking application that tracks customer balances. The balances are mutated when deposit/withdrawal transactions occur. Consider if the application only stores transactions - to return a customer's balance, the application adds up all previous transactions. This does not require mutable variables, however the memory and processing power required scales infinitely.

This is the concept behind **event sourcing** - storing the transactions but not the state. If state is requested, simply apply all transactions from the beginning.

Shortcuts can be taken, like saving state every midnight - state is then all transactions since last midnight.
The data storage required for this scheme will be large.
**Note: nothing ever gets deleted or updated from this type of data store.** As a result, there cannot be any concurrency update issues.
Source control systems are built on this concept.
