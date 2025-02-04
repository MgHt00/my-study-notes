[G]
* **Concise Form:** When an arrow function has only one expression, you can omit the curly braces `{}` and the `return` keyword. The expression itself is implicitly returned.

* **Curly Braces and Explicit Return:** When you use curly braces `{}` within an arrow function, it signifies a block of code. In this case, you **must** use the `return` keyword to explicitly specify the value that the function should return.

**Example:**

```javascript
// Implicit Return (no curly braces)
const square = x => x * x; 

// Explicit Return (with curly braces)
const add = (x, y) => { 
  return x + y; 
};
```

**In the context of your original question:**

* **`.catch(e => wait(500).then(queryDatabase))`:** This line works correctly because it uses the concise form of the arrow function. The expression `wait(500).then(queryDatabase)` is implicitly returned, and this expression itself returns a Promise.

* **`.catch(e => { wait(500).then(queryDatabase) })`:** This line returns `undefined` because the curly braces indicate a block of code. Without the `return` keyword, the function implicitly returns `undefined`.

I hope this further clarifies the concept of implicit and explicit returns in arrow functions!
