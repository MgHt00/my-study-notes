Yes, function expressions can be used without assigning them to a variable, which means the function is defined and invoked immediately without being stored. This is called an **immediately invoked function expression** (IIFE). Here's an example:

### Example of IIFE (Immediately Invoked Function Expression)

```javascript
(function() {
    console.log("This is an IIFE: I am invoked immediately!");
})();
```

In this example:
- A function expression is wrapped in parentheses: `(function() {...})`.
- Immediately after the closing parenthesis of the function expression, another pair of parentheses `()` is used to invoke it.
- The function is **not** assigned to any variable or constant but is immediately executed after its definition.

### Another Example with Parameters

```javascript
(function(name) {
    console.log(`Hello, ${name}!`);
})("Alice");
```

In this example:
- The function expression takes a parameter `name`.
- It is immediately invoked with the argument `"Alice"`, printing `Hello, Alice!` to the console.

### Explanation:
- These functions **do not declare a variable** to hold the function reference. Instead, they are executed right away after being defined.
- Since they're not assigned to a variable or constant, you **cannot invoke them again**.

IIFEs are commonly used to create private scopes and avoid polluting the global namespace.
