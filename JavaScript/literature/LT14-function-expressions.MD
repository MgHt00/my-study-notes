Function expressions in JavaScript provide several advantages over function declarations, depending on the context. Here are some key purposes and benefits of using function expressions:

### 1. **Anonymous Functions**
   - Function expressions can be **anonymous**, meaning they don’t need a name. This is useful for situations where a function is used once or needs no specific identifier, such as when passing functions as arguments to other functions:
     ```javascript
     setTimeout(function() {
         console.log("Hello after 1 second!");
     }, 1000);
     ```

### 2. **Assigning Functions to Variables**
   - You can assign function expressions to variables, which gives flexibility in storing, passing, or reusing functions:
     ```javascript
     const greet = function(name) {
         return `Hello, ${name}!`;
     };
     console.log(greet("Alice"));  // "Hello, Alice!"
     ```
   
### 3. **Using Functions as Arguments (Callbacks)**
   - Function expressions are commonly used as **callback functions**, which are passed into other functions to customize behavior:
     ```javascript
     const numbers = [1, 2, 3, 4];
     const doubled = numbers.map(function(num) {
         return num * 2;
     });
     console.log(doubled);  // [2, 4, 6, 8]
     ```

### 4. **Creating Closures**
   - When a function expression is created within another function, it **creates a closure**, capturing variables from its surrounding scope. This can be used for data encapsulation:
     ```javascript
     function counter() {
         let count = 0;
         return function() {
             count++;
             return count;
         };
     }
     const increment = counter();
     console.log(increment());  // 1
     console.log(increment());  // 2
     ```

### 5. **Control Over When a Function Is Defined**
   - Function expressions are only **defined at runtime** where the expression is reached in the code, making them more flexible and controllable than declarations, which are hoisted to the top of their scope.
     ```javascript
     const sayHello = function() {
         console.log("Hello!");
     };
     sayHello();  // Works here because it's defined above

     // sayGoodbye(); // Uncaught ReferenceError: Cannot access 'sayGoodbye' before initialization
     const sayGoodbye = function() {
         console.log("Goodbye!");
     };
     ```

### 6. **Self-Invoking Functions (IIFE)**
   - Function expressions allow **Immediately Invoked Function Expressions** (IIFE), which are often used to create a local scope for variables and avoid polluting the global scope:
     ```javascript
     (function() {
         const message = "Hello from IIFE!";
         console.log(message);
     })();
     // message is not accessible outside
