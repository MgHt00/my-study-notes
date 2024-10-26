A **closure** in JavaScript refers to a function that "remembers" the environment (the scope) in which it was created, even after that scope has exited. This means that a function can access variables from its outer (enclosing) scope even after the outer function has finished execution.

When you hear the phrase "JavaScript functions are closures," it means that every function in JavaScript inherently carries the surrounding context (or "closure") where it was defined, allowing it to reference variables and arguments from that scope later.

### Key Concepts:
1. **Lexical Scoping**: JavaScript uses lexical scoping, which means the function's scope is determined by where it's written in the code (not where it's executed). When a function is created, it keeps track of its surrounding scope.
   
2. **Function Inside Function**: When you define a function inside another function, the inner function has access to the variables of the outer function, even if the outer function has already returned.

3. **Persistent State**: A closure allows functions to "remember" the values of variables that existed in their scope at the time of creation.

### Basic Example of a Closure:
```javascript
function outer() {
  let outerVar = "I'm outside!";
  
  function inner() {
    console.log(outerVar); // The inner function "remembers" outerVar
  }
  
  return inner;
}

const closureFunc = outer();
closureFunc();  // Output: "I'm outside!"
```

- Here, `inner()` is a closure because it has access to `outerVar`, even though the outer function (`outer()`) has already finished execution.
- When we call `closureFunc()`, it still remembers the value of `outerVar` from the time it was defined.

### Practical Use of Closures:

1. **Encapsulation**: You can use closures to hide implementation details and create private variables.
   
   ```javascript
   function createCounter() {
     let count = 0;
     return function() {
       count++;
       return count;
     };
   }
   
   const counter = createCounter();
   console.log(counter());  // 1
   console.log(counter());  // 2
   console.log(counter());  // 3
   ```
   
   - The inner function returned by `createCounter()` has access to `count`, even though `createCounter()` has already finished. The variable `count` is now encapsulated within the closure, acting as a private variable.

2. **Callback Functions**: Closures are commonly used in asynchronous code or event-driven programming. For example, when you define a callback function in event listeners or timers, it forms a closure with the surrounding state.

   ```javascript
   function createTimer(delay) {
     let message = `You waited for ${delay} milliseconds!`;
     
     setTimeout(function() {
       console.log(message);  // The inner function remembers 'message'
     }, delay);
   }

   createTimer(2000);  // After 2 seconds, logs: "You waited for 2000 milliseconds!"
   ```

### Why Are Closures Powerful?
- **State Persistence**: Variables can persist across function calls, providing a mechanism to maintain state between executions of a function.
- **Data Privacy**: Variables inside a closure are not directly accessible from outside, which helps in creating private variables.
- **Functional Programming**: Closures are fundamental in many JavaScript patterns, especially functional programming (e.g., higher-order functions like `map()`, `reduce()`, and `filter()`).

### Example: Loop with Closure Problem
One common mistake people make is with loops and closures. For example, when using `var` in loops to create closures, you can run into problems because `var` is function-scoped.

```javascript
for (var i = 1; i <= 3; i++) {
  setTimeout(function() {
    console.log(i);
  }, 1000);
}

// Output after 1 second:
// 4
// 4
// 4
```
In this example, `var i` is not block-scoped, so all functions inside `setTimeout` share the same `i`. However, using closures or `let`, you can fix this:

```javascript
for (let i = 1; i <= 3; i++) {
  setTimeout(function() {
    console.log(i);
  }, 1000);
}

// Output after 1 second:
// 1
// 2
// 3
```

Here, `let` creates a block-scoped variable that the closure captures individually for each iteration.

### Conclusion:
Closures are a powerful feature of JavaScript that allows functions to "remember" the scope in which they were created. This is crucial for many advanced JavaScript patterns, like callbacks, encapsulation, and maintaining state across function calls. It's one of the foundational concepts that make JavaScript both flexible and powerful!
