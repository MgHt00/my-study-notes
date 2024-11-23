The authors' statement, "Because static methods are invoked on the constructor rather than on any particular instance, it almost never makes sense to use the `this` keyword in a static method," reflects an important distinction between **static methods** and **instance methods** in JavaScript.

Let me break it down for you:

---

### 1. **Static Methods**
- **Definition**: Static methods are defined on the class itself, not on its instances. You call them using the class name, e.g., `ClassName.methodName()`.
- **Purpose**: They typically perform utility-like tasks that don't depend on the state of any particular instance.

### Why `this` in a Static Method Doesn't Make Sense
- In a static method, `this` refers to the **class itself**, not an instance. 
- Static methods are not tied to the properties or behavior of any specific instance. So, using `this` to access instance-specific properties in a static method would lead to errors because there is no instance involved.

#### Example of Misusing `this` in a Static Method:
```javascript
class Example {
    static myStaticMethod() {
        console.log(this.instanceProperty); // ❌ This will not work because `this` refers to the class, not an instance
    }
}

Example.myStaticMethod(); // undefined, since `this` refers to Example, which has no instanceProperty
```

---

### 2. **When `this` is Useful in Static Methods**
There are rare cases where `this` is meaningful in static methods, specifically when:
- You want to refer to the class itself (not an instance).
- You use `this` to make a static method or property inheritable by subclasses.

#### Example: Using `this` in Static Methods for Subclassing
```javascript
class Parent {
    static staticValue = "Hello from Parent";

    static getStaticValue() {
        return this.staticValue; // Refers to the class calling the method
    }
}

class Child extends Parent {
    static staticValue = "Hello from Child";
}

console.log(Parent.getStaticValue()); // Output: "Hello from Parent"
console.log(Child.getStaticValue());  // Output: "Hello from Child"
```
Here, the `this` keyword refers to the class (`Parent` or `Child`) that invoked the static method. This flexibility allows static methods to behave differently in subclasses.

---

### 3. **Why `this` Wasn't Needed in Your Code**
In your earlier example:
```javascript
class Global extends GlobalMethods {
    static getDummyValue() {
        return 3; // Directly returns a value without referencing `this`
    }
}
```

- `getDummyValue()` simply returns a value (`3`) and does not depend on any property of the class (`this`) or any instance.
- Since no reference to the class or its static properties is required, there’s no need for `this` here.

If you wanted to make `dummyValue` a **static class property**, then using `this` would make sense:

```javascript
class Global {
    static dummyValue = 3; // Static property

    static getDummyValue() {
        return this.dummyValue; // `this` refers to the class, accessing `dummyValue`
    }
}

console.log(Global.getDummyValue()); // Output: 3
```

---

### 4. **Instance Methods vs. Static Methods**
| Feature               | Instance Method                     | Static Method                        |
|-----------------------|-------------------------------------|--------------------------------------|
| **Invocation**        | On an instance (`instance.method()`) | On the class (`Class.method()`)      |
| **`this` Context**    | Refers to the instance              | Refers to the class itself           |
| **Access**            | Can access instance and class properties | Can only access class properties    |
| **Example Use**       | Object-specific behavior (e.g., `calculate()`) | Shared utilities (e.g., `isType()`) |

---

### 5. **Takeaway**
The authors are emphasizing that **static methods are not tied to instances** and hence rarely need `this`—which is primarily used for instance-specific or inheritance-aware scenarios. In cases where you use static properties or inheritance, `this` in static methods can be meaningful, but for simple use cases, you can omit it altogether. 😊
