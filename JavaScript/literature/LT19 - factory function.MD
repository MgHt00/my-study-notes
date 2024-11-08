A **factory function** is a function that creates and returns a new object, without needing the `new` keyword. It’s a pattern that gives flexibility in object creation, and it’s a great alternative to using classes, especially when you don’t need the extra structure of a class or when you want more control over the object creation process.

Here's a breakdown of factory functions:

### Why Use a Factory Function?
- **Simplicity**: Factory functions are often easier to understand and use than classes, especially for simpler objects.
- **Avoiding `new`**: No need to worry about using `new` and possibly forgetting it, which can cause issues in constructor functions.
- **Flexible Return Values**: They can return any kind of object, including enhanced or customized objects.
- **Encapsulation**: They can create private variables by taking advantage of closures.

### Basic Example
Here's a simple factory function that creates a person object:

```javascript
function createPerson(name, age) {
  return {
    name: name,
    age: age,
    greet() {
      console.log(`Hello, my name is ${this.name} and I am ${this.age} years old.`);
    }
  };
}

const person1 = createPerson("Alice", 30);
person1.greet();  // Outputs: Hello, my name is Alice and I am 30 years old.
```

In this example:
- `createPerson` is a factory function.
- It returns a new object with `name`, `age`, and a `greet` method every time it’s called.

### Advantages Over Constructor Functions
1. **No `new` Required**: Just calling the factory function returns an object, so there’s no risk of missing `new`.
2. **Encapsulation**: Factory functions allow for private variables, which aren’t as straightforward with classes or constructor functions.

### Example with Private Variables
By using closures, factory functions can create “private” variables, which can’t be accessed outside of the function:

```javascript
function createBankAccount(owner, initialBalance) {
  let balance = initialBalance; // Private variable

  return {
    owner: owner,
    deposit(amount) {
      balance += amount;
      console.log(`Deposited ${amount}. New balance is ${balance}.`);
    },
    withdraw(amount) {
      if (amount > balance) {
        console.log("Insufficient funds.");
      } else {
        balance -= amount;
        console.log(`Withdrew ${amount}. New balance is ${balance}.`);
      }
    },
    getBalance() {
      return balance;  // Only way to access balance
    }
  };
}

const account = createBankAccount("John", 1000);
account.deposit(500); // Deposited 500. New balance is 1500.
account.withdraw(200); // Withdrew 200. New balance is 1300.
console.log(account.balance); // undefined (balance is private)
```

### Factory Functions vs. Classes
Factory functions are often preferred when:
- You don’t need inheritance.
- You want more control over how objects are created.
- You need encapsulation for private data (as in the bank account example).

Classes are more common when:
- You need inheritance.
- You want a more structured approach, particularly for complex objects.

### Summary
A factory function:
- Is simply a function that returns a new object.
- Provides flexibility, encapsulation, and ease of use.
- Works well for creating objects, particularly if you don’t need the power of a class. 

---

<em>So it is because the factory function is returning an object, we don't need to use the keyword new with the object creation? </em>

Yes, exactly! In a factory function, **because it directly returns an object**, there’s no need to use the `new` keyword. 

Here’s why this works:

- The `new` keyword is specifically used to call a **constructor function**, which creates a new empty object, sets up the prototype chain, and binds `this` to that new object.
- In contrast, a factory function **handles the entire object creation process internally**, so there’s no need for `new` to set up the object.

When the factory function is called, it already knows to return a fully formed object without relying on any special behavior from `new`. You simply call the function, and it returns an object.

### Example to Show the Difference

With a **constructor function**:

```javascript
function Person(name) {
  this.name = name;
}

// You must use `new` here to create an instance of Person
const person1 = new Person("Alice");
console.log(person1.name); // Outputs: Alice
```

If you omit `new` here (`const person1 = Person("Alice");`), `this` would not refer to the new object, and you’d end up assigning `name` to the global scope or `undefined`.

With a **factory function**:

```javascript
function createPerson(name) {
  return { name: name }; // Directly returns an object
}

const person2 = createPerson("Bob"); // No `new` required
console.log(person2.name); // Outputs: Bob
```

Since `createPerson` is a factory function that returns an object directly, it doesn’t need `new`—you can just call it like any other function.

### Why This Matters
Avoiding `new` can help prevent mistakes, especially since **forgetting `new` with a constructor function can lead to unexpected bugs** (like assigning to the global scope). Factory functions make object creation straightforward and eliminate this potential error. 

Let me know if you'd like more examples to clarify further!

--

<em>Factory functions are often preferred when: * You don’t need inheritance.</em>

<em>Can you explain me more about this?</em>

Absolutely, I'd be happy to dive into that!

Factory functions are often chosen when your object doesn’t need inheritance, as they simply create and return new objects without using the `new` keyword. This style can be useful when:

1. **Simplicity**: If your objects don’t require inheritance or complex setup, factory functions are straightforward and avoid some of the pitfalls of the `this` context with `new`.
2. **Avoiding `this` and `new`**: Factory functions don’t use `this`, so there's less concern about accidentally creating objects without `new` (which could happen with constructor functions). This can make the code more flexible and less error-prone.
3. **Return Values**: Unlike constructors, factory functions aren’t limited to only returning instances of a class—they can return different types of objects or even primitives based on conditions, which adds flexibility.
4. **Encapsulation**: By defining private variables within a factory function (with `let` or `const` inside), you can hide data that isn’t accessible outside of the function, helping you better encapsulate functionality without exposing all details of an object.

Here's an example to illustrate:

```javascript
function createUser(name, age) {
  // Private variables
  let isAdmin = false;

  return {
    name,
    age,
    getRole() {
      return isAdmin ? "Admin" : "User";
    },
    promoteToAdmin() {
      isAdmin = true;
    },
  };
}

const user1 = createUser("Alice", 25);
user1.promoteToAdmin();
console.log(user1.getRole()); // "Admin"
```

In this example:
- The `createUser` function creates an object with `name`, `age`, and a few methods.
- The `isAdmin` variable is private to the function scope and can only be accessed or modified through `getRole` and `promoteToAdmin`.
- There’s no need for `new`, and `this` isn’t involved.

This style keeps `isAdmin` private, avoiding the need for inheritance structures when it’s not necessary. In short, factory functions are a flexible, often simpler alternative for object creation when the complexity of `new` and prototype chains isn’t required.
