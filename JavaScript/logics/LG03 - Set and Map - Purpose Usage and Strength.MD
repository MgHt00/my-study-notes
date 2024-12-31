The reason you cannot delete the array `[1, 2, 3]` from the set in your code is due to how JavaScript handles object references, including arrays. Here's a detailed explanation:

### Key Concept: Objects and Arrays are Compared by Reference
- When you add an array (`[1, 2, 3]`) to the `Set`, JavaScript stores a reference to that specific array object, not just its contents.
- Later, when you attempt to delete `[1, 2, 3]`, you are creating a **new array object** (with the same values) and passing it to the `delete` method.
- These two array objects, despite having the same elements, are not considered the same because they occupy different locations in memory.

### Demonstration of Object References
```javascript
let a = [1, 2, 3];
let b = [1, 2, 3];
console.log(a === b); // false: different array objects
```
Even though `a` and `b` contain identical elements, they are different objects because their references are not the same.

### How it Relates to Your Code
```javascript
let s = new Set();
let arr = [1, 2, 3];
s.add(arr);            // Adds the reference to `arr` to the set
s.delete([1, 2, 3]);   // Attempts to delete a different array object
// This fails because `[1, 2, 3]` is not the same object as `arr`.
```

### Fixing the Issue
To delete the array, you must use the exact same reference as the one used when adding it to the set:
```javascript
let s = new Set();
let arr = [1, 2, 3];
s.add(arr);            // Add the array to the set
s.delete(arr);         // Use the same reference to delete it
console.log(s.has(arr)); // false: the array is removed
```

### Key Takeaway
In JavaScript:
- Primitive values (e.g., numbers, strings) are compared by value.
- Objects and arrays are compared by reference. For operations like `Set.prototype.delete`, you must use the exact same reference used when adding the object to the set.
