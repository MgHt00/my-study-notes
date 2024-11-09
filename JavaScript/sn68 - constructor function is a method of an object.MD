Yes, you’re understanding it well! When the constructor function is a method of an object, like `o.m`, you access it through that object. However, when you use `new o.m()`, the `new` keyword creates a new instance independently of `o`. So `o` is only used as a way to locate the constructor function (like `o.m`), but it doesn't affect the new instance being created.

Here's a breakdown:

- **Accessing the constructor**: Since the constructor function `m` is stored as a method on `o`, you use `o.m` to refer to it.
- **Using `new o.m()`**: The `new` keyword tells JavaScript to create a new object and set `this` to that new object within `m`. In this context, `o` is only used to locate the function `m`, and nothing about `o` itself is passed into the new instance.
  
To put it simply, `o.m()` just gives you a way to reach `m` for the `new` invocation, but it doesn't influence the new instance created. The new instance is entirely the result of the `m` constructor function.

---

**Using `new o.m()`**: The `new` keyword tells JavaScript to create a new object and set `this` to that new object within `m`.

---

When we use `new` with a function, JavaScript interprets it as a request to:

1. **Create a new object**.
2. **Assign that new object** to `this` within the function so that it becomes the context for any properties or methods added in the function.
3. **Return the new object** automatically, even if there’s no `return` statement.

When we have something like `new o.m()`, there are two parts at play:

1. **Locating the Constructor Function**: `o.m` tells JavaScript where to find the function. In this case, `m` is a method on `o`. The object `o` is essentially a “container” for `m`, but it doesn’t impact the new instance itself.
   
2. **Creating a New Instance with `new`**: When we use `new o.m()`, the `new` keyword creates a fresh object and sets `this` to refer to that object within `m`. This means that any properties or methods added to `this` inside `m` are added to the new object, **not** to `o`.

### Example

Here’s an example to illustrate:

```javascript
const o = {
  m: function() {
    this.property = "I’m a new instance property";
  }
};

// Creating a new instance using `new o.m()`
const newInstance = new o.m();

// `newInstance` now has the property we defined in `m`
console.log(newInstance.property);  // Outputs: "I’m a new instance property"

// `o` itself remains unchanged
console.log(o.property);  // Outputs: undefined
```

In this example:
- **Locating `m`**: `o.m` helps us access the `m` function.
- **Creating a new instance**: Using `new o.m()` tells JavaScript to create a new instance. Inside `m`, `this` refers to this new instance, so when we write `this.property = ...`, it adds `property` to `newInstance`, not `o`.

**Key takeaway**: The `new` keyword ignores `o` after finding `m` and uses `m` to create a brand-new object where `this` refers to the new instance. The original object (`o`) is not part of the instance creation process beyond giving us access to `m`.
