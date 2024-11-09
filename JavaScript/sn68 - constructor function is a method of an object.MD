Yes, you’re understanding it well! When the constructor function is a method of an object, like `o.m`, you access it through that object. However, when you use `new o.m()`, the `new` keyword creates a new instance independently of `o`. So `o` is only used as a way to locate the constructor function (like `o.m`), but it doesn't affect the new instance being created.

Here's a breakdown:

- **Accessing the constructor**: Since the constructor function `m` is stored as a method on `o`, you use `o.m` to refer to it.
- **Using `new o.m()`**: The `new` keyword tells JavaScript to create a new object and set `this` to that new object within `m`. In this context, `o` is only used to locate the function `m`, and nothing about `o` itself is passed into the new instance.
  
To put it simply, `o.m()` just gives you a way to reach `m` for the `new` invocation, but it doesn't influence the new instance created. The new instance is entirely the result of the `m` constructor function.
