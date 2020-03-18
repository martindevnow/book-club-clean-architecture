## Chapter 5: Object-Oriented Programming

What is OO? One common answer is "The combination of data and function." This is not correct because it implies `o.f()` is different than `f(o)`. Another common answer is "A way to model the real world."

OO can be explained by 3 concepts: _encapsulation_, _inheritance_ and _polymorphism_.

### Encapsulation

OO languages provide easy and effective encapsulation of data and functions by grouping cohesive sets of data and functions. Outside their groups, data is hidden and only some functions are known. This can be seen in practice as private data members and public member functions of a class.

The C language natively supports perfect encapsulation through header and implementation files. Subsequent languages like Java or C++ do not enforce encapsulation as strongly, due to technical or other reasons. Specific keywords like _public_, _private_ and _public_ were hacks these languages implemented to retain encapsulation enforcement.

### Inheritance

Can be explained as the redeclaration of a group of variables or functions within an enclosing scope.

### Polymorphism

Is an application of pointers to functions. However, this is dangerous because use is driven by a set of manual conventions:

- You must follow the convention to initialize those pointers
- You must follow the convention to call your functions through those pointers

Failure to adhere to the conventions can create nasty bugs. OO languages eliminate these conventions.

For example, programmers used to write code that read input from decks of cards. Later on magnetic tape was used instead of cards. It would be convenient if programs were agnostic of cards or tape instead of re-writing large parts of the source code.

### Dependency Inversion

Any source code dependency, no matter where it is, can be inverted. Any dependency can be inverted by inserting an interface between them. This gives architects absolute control over the direction of source code dependencies in the system.

Example 1:

```
// Without Dependency Inversion

$.get('/url/to/data', data => {
    $('selector1').text(data.prop1);
    $('selector2').text(data.prop2);
});


// With Dependency Inversion

fillFromServer('/url/to/data', view);

function fillFromServer(url, view) {
    $.get(url, data => {
        view.setValues(data);
    });
}

const view = {
    setValues: data => {
        $('selector1').text(data.prop1);
        $('selector2').text(data.prop2);
    }
};

```

Example 2: `UI --> Business Rules <-- Database`

Dependency Inversion can rearrange the dependency flow here. The UI and database can be plugins to the business rules. The source code of the business rules doesn't mention the UI or database. As a result, all 3 can be compiled separately, into separate components or deployment units (jar, DLL, Gem, etc.).
Business rules can be deployed _independently_ of the UI and database.
Changes to the UI or database do not have an effect on the business rules.

When the source code in a component changes, only that component needs to be redeployed. This is called **independent deployability**.
When the modules in the system can be deployed independently, they can be developed by different teams. This is called **independent developability**.

OO leverages polymorphism to control source code dependency within the system. The architect creates a plugin architecture: modules that contain high-level policies are independent of modules that contain low-level details. Low-level detail plugin modules can be deployed and developed independently from the modules that contain high-level policies.
