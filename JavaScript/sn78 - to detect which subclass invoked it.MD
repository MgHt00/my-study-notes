Let's break down the passage you're referring to, and I'll clarify it step by step.

### What is `new.target`?

In JavaScript, when you call a function with the `new` keyword, it creates a new instance of an object and executes the constructor function. Normally, inside the constructor function, `this` refers to the newly created object. However, there’s a special keyword `new.target` that gives you the constructor function that was directly invoked.

- **When `new.target` is undefined**: This happens if the constructor function is called *without* `new`. For example, if you call a constructor function like a regular function, `new.target` will be `undefined`.

- **When `new.target` is defined**: This happens when the constructor is called with the `new` keyword. In this case, `new.target` refers to the constructor function that was used to create the object.

### What happens with subclasses and `super()`?

In a subclass, when you invoke the parent class's constructor using `super()`, JavaScript behaves differently. The `super()` call is how the subclass invokes the parent class's constructor. Here’s the key detail: **when a subclass constructor calls `super()`, `new.target` inside the parent class constructor refers to the subclass, not the parent class**. 

This is because `new.target` gets the constructor of the function that was directly invoked. When you call `super()`, it indirectly calls the constructor of the subclass.

### Why is `new.target.name` useful?

In some situations, you might want to log which class constructor was actually invoked. For instance, imagine you want to track whether the object is being created by a subclass or the superclass, for debugging or logging purposes.

If the superclass's constructor logs `new.target.name`, it will print the name of the subclass, even though the code is in the parent class. This allows you to capture the actual class that was instantiated, even if it’s a subclass.

### Example Code

```javascript
class Animal {
  constructor() {
    console.log("Animal constructor");
    console.log(new.target.name);  // Logs the name of the class calling this constructor
  }
}

class Dog extends Animal {
  constructor() {
    super();
    console.log("Dog constructor");
  }
}

let d = new Dog();
// Output:
// Animal constructor
// Dog
// Dog constructor
```

In this example:
- The `Animal` class constructor calls `new.target.name`. 
- Even though the `super()` call is in the `Dog` subclass, `new.target` in the `Animal` constructor refers to `Dog` because `Dog` was the class that was actually instantiated.
- This demonstrates how `new.target.name` can give you useful information about the subclass calling the superclass constructor.

### Conclusion

In short, `new.target` helps track which constructor is being invoked, and when a subclass calls `super()`, the superclass can still detect which subclass invoked it using `new.target`. This can be useful for logging or debugging, but typically a well-designed superclass doesn't need to care about being subclassed unless you specifically want to track that behavior.
