Sure! Here's a quick example to demonstrate what the authors mean when they say that if the argument to `search()` is not a regular expression, it gets converted into one using the `RegExp` constructor.

### Example Code

```javascript
let str = "Hello, world!";

// Using a string argument
let result1 = str.search("world");
console.log(result1); // Output: 7

// Equivalent to passing a RegExp object
let result2 = str.search(/world/);
console.log(result2); // Output: 7

// Let's verify the conversion
let stringArg = "world";
let regexFromString = new RegExp(stringArg);
console.log(regexFromString); // Output: /world/
```

### Explanation

- In `str.search("world")`, even though `"world"` is a **string**, it is automatically converted into a regular expression by JavaScript. Internally, it's like calling `new RegExp("world")`.
  
- In `str.search(/world/)`, you're explicitly passing a **regular expression**.

The results are the same because JavaScript performs the conversion seamlessly in the background.

This automatic conversion only happens in methods like `search()`, which expect a regular expression. If you pass a string, the method converts it into a `RegExp` object using the `RegExp` constructor.
