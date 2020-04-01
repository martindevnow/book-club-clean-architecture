## ISP: The Interface Segregation Principle

<img width="570" alt="10-1" src="https://user-images.githubusercontent.com/16246749/78095207-5ff5da80-73a4-11ea-86e8-fa758f06c1a3.png">

The chapter start with an sample: there are several users who use the operations of the `OPS` class. Let’s assume that `User1` uses only `op1`, `User2` uses only `op2`, and `User3` uses only `op3`.

Also, imagine that `OPS` is a class written in a statically typed language like Java. In that case, the source code of `User1` will depend on `op2` and `op3`, even though it doesn’t call them. This dependence means that a change to the source code of `op2` in `OPS` will force `User1` to be recompiled and redeployed, even though nothing that it cared about has actually changed.

The author present this situation and a solution: it can be resolved by `segregating the operations into interfaces` as shown in the next figure:

<img width="433" alt="10-2" src="https://user-images.githubusercontent.com/16246749/78095639-6e90c180-73a5-11ea-8a21-3cecd654f46b.png">

In this new situation the source code of `User1` will depend on `U1Ops`, and `op1`, but will not depend on `OPS`. Thus a change to `OPS` that `User1` does not care about will not cause `User1` to be recompiled and redeployed.

### ISP and Languages

Statically typed languages like Java force programmers to create declarations that users must `import`, or `use`, or otherwise `include`. 
These `included` declarations create the source code dependencies that force recompilation and redeployment.

In dynamically typed languages like Ruby and Python, doesn't have this declarations in source code because they are inferred at runtime. 
Thus there are no source code dependencies to force recompilation and redeployment. 
As a conclusion we have that `dynamically typed languages` create systems that are more flexible and less tightly coupled than `statically typed languages`.

But ISP is not only a language issue.

### ISP and Architecture

In general, it is harmful to depend on modules that contain more than you need.

In architectural level ISP is also considered.

If you're working on a `System S` and you want to include a `Framework F`, and suppose that the authors of F have bound it to a `Database D`. 
So S depends on F. which depends on D.

<img width="883" alt="10 3" src="https://user-images.githubusercontent.com/16246749/78096704-540c1780-73a8-11ea-9c0f-29b59812ed6c.png">

If D contains features that F does not use and S does not care about, changes on those features may force the redeployment of F and S.
In a worst case, can cause a failure in all levels.

### Conclusion

Depending on something that carries baggage that you don’t need can cause you troubles that you didn’t expect.
