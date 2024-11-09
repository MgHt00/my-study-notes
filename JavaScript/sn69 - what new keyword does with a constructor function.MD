The authors are explaining how the `new` keyword automates some of the work that would otherwise be required to set up a new object when using a constructor function like `Range`. Here's a breakdown of what’s happening when you use `new` with the `Range` constructor:

1. **Automatic Creation of a New Object**: When you write `new Range(from, to)`, JavaScript automatically:
   - Creates a new, empty object (let’s call it `newObject`).
   - Links `newObject` to the prototype of `Range` by setting `newObject.__proto__` to `Range.prototype`, so `newObject` inherits any methods or properties on `Range.prototype`.
   - Assigns `newObject` to `this` inside the `Range` function, making `this` refer to `newObject`.

2. **Initializing Properties on `this`**: Inside `Range`, `this` refers to the new object (`newObject`), so when we write:
   ```javascript
   this.from = from;
   this.to = to;
   ```
   we’re adding `from` and `to` as properties on the new object created by `new`. This step "initializes" the object with values specific to this instance of `Range`.

3. **Automatic Return of `this`**: After running the code in `Range`, the new object (`newObject`) is automatically returned as the result of `new Range(from, to)`. No `return` statement is needed in the constructor because `new` handles the return of the initialized object.

### Without `new`
If we didn't use `new`, we’d need to create the new object and assign it manually. For example, we might have to write something like this:

```javascript
function Range(from, to) {
  const obj = Object.create(Range.prototype);  // Step 1: Create a new object and link its prototype
  obj.from = from;                             // Step 2: Initialize properties
  obj.to = to;
  return obj;                                  // Step 3: Return the new object
}
```

The `new` keyword automates these steps, making it simpler to write constructors. So, instead of manually creating an object and linking it to the prototype, we just write:

```javascript
const r = new Range(1, 5);
```

### Summary
Using `new` with a constructor function:
- **Creates** a new object.
- **Sets `this`** in the constructor to refer to the new object.
- **Links** the new object to the constructor’s prototype (`Range.prototype`).
- **Returns** the new object automatically. 

All you have to do is initialize the properties you need on `this` in the constructor!
