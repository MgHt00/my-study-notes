This passage is explaining why regular JavaScript functions can be used as **constructors** and what it means when we talk about a function’s **prototype property** and the **constructor** property.

### 1. Regular Functions as Constructors
In JavaScript, any regular function (excluding arrow functions, generator functions, and async functions) can be used to create objects when called with the `new` keyword. When you call a function with `new`, it acts as a **constructor function**, setting up a new object and initializing its properties.

### 2. Prototype Property
Every regular JavaScript function automatically has a special property called `prototype`. This `prototype` property is:
   - An object that is used as the prototype for instances created by the function when it’s used as a constructor with `new`.
   - Important because it contains shared methods or properties that all instances created by that constructor will inherit.

Let’s look at an example:
```javascript
let F = function() {};
```

Here, `F` is a regular function, so JavaScript automatically gives it a `prototype` property:
- `F.prototype` points to an object that will be used as the prototype for any object created with `new F()`.

### 3. Constructor Property
The `prototype` object itself has a property called `constructor`, which:
   - Points back to the function (`F`) that this prototype is associated with.
   - Allows instances to "know" which constructor function created them.

To illustrate this with your example:

![My own illustration](https://github.com/MgHt00/my-study-notes/blob/main/JavaScript/_assets/20241110_091422.jpg?raw=true)

```javascript
let F = function() {};   // Define a function F
let p = F.prototype;     // Get F’s prototype object
let c = p.constructor;   // Get the constructor property of F’s prototype
```

- Here, `p` is `F.prototype`, which is an object automatically created by JavaScript.
- `p.constructor` is a reference back to `F` itself.

So:
```javascript
c === F; // true
```

This confirms that the `constructor` property of `F.prototype` points back to `F`, linking the prototype to its function.

### 4. Why This Matters
This setup allows us to check an object’s constructor:
- When we create an instance with `new F()`, JavaScript sets up that instance’s prototype to be `F.prototype`.
- The `constructor` property on `F.prototype` lets us trace instances back to `F`.

### Example Putting It All Together
Let’s see how this works with an instance:

```javascript
function F() {}           // Define function F
let obj = new F();        // Create an instance of F

console.log(obj.__proto__ === F.prototype);  // true
console.log(obj.constructor === F);          // true
```

- `obj.__proto__` points to `F.prototype`, so `obj` inherits any properties on `F.prototype`.
- `obj.constructor` is `F`, thanks to the `constructor` property in `F.prototype`.

### Summary
1. **Prototype**: `F.prototype` is an object that new instances of `F` will inherit from.
2. **Constructor Property**: `F.prototype.constructor` points back to `F`, creating a circular reference that links instances to their original constructor.
3. **Automatic Setup**: JavaScript automatically gives every regular function a `prototype` object and a `constructor` property within that prototype, setting up inheritance without additional code. 

This is the basis for JavaScript’s prototype-based inheritance. Does this make things clearer?
