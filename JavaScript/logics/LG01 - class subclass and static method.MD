Your logic is on the right track, but there are a couple of syntax issues and logical mistakes in your code. I'll explain and correct them below while confirming whether your understanding aligns with proper usage:

---

### Issues in the Code

1. **Syntax Error:**
   - `newGlobal()` is missing a space. It should be `new Global()`.

2. **`document.queryselector` typo:**
   - JavaScript methods are case-sensitive. The correct method is `document.querySelector` (capital "S").

3. **`dummyValue` in `getDummyValue()` method:**
   - `dummyValue` is not defined within the static method. To access `dummyValue`, you need to reference it through an instance (`this.dummyValue`) or explicitly make it static at the class level.

4. **Calling static methods:**
   - `getDummyValue()` is a static method, so it is correctly accessed through the class `Global`, not an instance.

---

### Corrected Code

```javascript
class GlobalMethods {
    buildNode() {
        // Codes to build a node
        console.log("Building a node...");
    }

    clearNode() {
        // Codes to clear a node
        console.log("Clearing a node...");
    }
}

class Global extends GlobalMethods {
    constructor() {
        super(); // Call the parent class (GlobalMethods) constructor if needed
        this.dummyValue = 3; // Instance property
        this.container = document.querySelector("#DOC"); // Corrected querySelector
    }

    static getDummyValue() {
        return 3; // Static value, accessible via the class, not instance
    }
}

const gMgr = new Global(); // Instantiate the class
gMgr.clearNode(); // Instance method, inherited from GlobalMethods
let gValue = Global.getDummyValue(); // Static method, called on the class
console.log(gValue); // Output: 3
```

---

### Key Points about the Correct Code:

1. **Inheritance:**
   - `Global` inherits methods from `GlobalMethods` via `extends`.
   - You correctly called `gMgr.clearNode()` because it is an instance method inherited from `GlobalMethods`.

2. **Static Methods:**
   - Static methods belong to the class itself, not to instances. Thus, `Global.getDummyValue()` works but `gMgr.getDummyValue()` would fail.

3. **Instance Properties:**
   - `this.dummyValue` is an instance property and requires an instance (`gMgr`) to access.

4. **`super()` in the constructor:**
   - Although `GlobalMethods` doesn't have its own constructor in this example, calling `super()` is still a good practice for classes inheriting from a parent. It ensures the parent class's constructor is invoked if defined.

---

### Enhancing the Example
To make `dummyValue` accessible both as an instance and static value:

```javascript
class Global extends GlobalMethods {
    static dummyValue = 3; // Static class property

    constructor() {
        super();
        this.dummyValue = Global.dummyValue; // Sync instance with static value
        this.container = document.querySelector("#DOC");
    }

    static getDummyValue() {
        return this.dummyValue; // Access the static class property
    }
}
```

Now you can do:

```javascript
console.log(Global.dummyValue); // 3
console.log(gMgr.dummyValue);   // 3
console.log(Global.getDummyValue()); // 3
```

---

### Final Thoughts
Your logic is solid and you're grasping important concepts about **class inheritance**, **static vs. instance properties/methods**, and **subclassing**. With small corrections, your code works and demonstrates a good understanding of these topics. Let me know if you'd like more clarification on any part! 😊
