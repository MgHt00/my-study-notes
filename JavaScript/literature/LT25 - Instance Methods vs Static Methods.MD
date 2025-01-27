### 4. **Instance Methods vs. Static Methods**
| Feature               | Instance Method                     | Static Method                        |
|-----------------------|-------------------------------------|--------------------------------------|
| **Invocation**        | On an instance (`instance.method()`) | On the class (`Class.method()`)      |
| **`this` Context**    | Refers to the instance              | Refers to the class itself           |
| **Access**            | Can access instance and class properties | Can only access class properties    |
| **Example Use**       | Object-specific behavior (e.g., `calculate()`) | Shared utilities (e.g., `isType()`) |

The term *instance method* isn't just a fancy word—it refers to a specific type of method in object-oriented programming that is tied to an **instance** of a class or object. Here's what it means in detail:

---

### What Is an Instance Method?
An *instance method* is a function that belongs to an **object instance** and can access that instance's properties and methods. In JavaScript, it typically:

- Operates on data specific to that instance.
- Can access the instance using the `this` keyword.
- Requires the object (or class instance) to be instantiated in order to call it.

---

### Why the Name "Instance Method"?
The term distinguishes it from:
1. **Static methods**: These belong to the class itself rather than to any object instance.
2. **Global or standalone functions**: Functions that are not associated with any specific class or object.

---

### Example of Instance Methods vs. Static Methods in JavaScript

```javascript
class Person {
  constructor(name) {
    this.name = name; // Instance property
  }

  // Instance method
  sayHello() {
    console.log(`Hello, my name is ${this.name}.`);
  }

  // Static method
  static greetEveryone() {
    console.log("Hello, everyone!");
  }
}

// Creating an instance of Person
const person1 = new Person("Alice");

// Calling the instance method
person1.sayHello(); // Output: "Hello, my name is Alice."

// Trying to call the instance method on the class itself (this won't work)
Person.sayHello(); // TypeError: Person.sayHello is not a function

// Calling the static method
Person.greetEveryone(); // Output: "Hello, everyone!"

// Trying to call the static method on an instance (this won't work)
person1.greetEveryone(); // TypeError: person1.greetEveryone is not a function
```

---

### Key Abilities of Instance Methods
1. **Access Instance Data**: They can use the `this` keyword to work with instance properties and methods.
   - Example: `this.name` in the `sayHello()` method refers to the specific `name` property of the object instance.
   
2. **Encapsulation**: They let you define behavior tied to specific objects, keeping the logic close to the data.

3. **Custom Behavior Per Instance**: Since they operate on an instance, their behavior can vary based on the instance's data.

---

### When to Use Instance Methods?
- When you need a function to operate on an instance's data or state.
- When the behavior depends on the specific object instance.
  
---
