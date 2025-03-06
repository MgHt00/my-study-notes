[G] You've picked up on a very subtle but important distinction in how different types of JavaScript declarations behave in non-module scripts. Let's illustrate it:

**1. `var` and `function` Declarations (Older Behavior)**

* **Global Object Properties:** When you declare variables with `var` or functions with `function` at the top level of a non-module script, they become properties of the global object (usually `window` in browsers).
* **Access via `window`:** You can access these variables and functions using `window.variableName` or `window.functionName()`.
* **Example:**

    ```html
    <!DOCTYPE html>
    <html>
    <head>
    <title>Var/Function Example</title>
    </head>
    <body>
    <script>
      var myVar = "Hello";
      function myFunction() {
        console.log("Function called");
      }
    </script>

    <script>
      console.log(window.myVar); // Output: Hello
      window.myFunction(); // Output: Function called
    </script>
    </body>
    </html>
    ```

**2. `const`, `let`, and `class` Declarations (Newer Behavior)**

* **Document Scope, Not Global Object:** When you declare variables with `const` or `let` or classes with `class` at the top level of a non-module script, they are scoped to the *document* (the script's execution context), but they are *not* added as properties of the global object.
* **Direct Access Only:** You can access these variables and classes directly by their names within the same document, but you cannot access them using `window.variableName` or `window.className`.
* **Example:**

    ```html
    <!DOCTYPE html>
    <html>
    <head>
    <title>Let/Const/Class Example</title>
    </head>
    <body>
    <script>
      let myLet = "World";
      const myConst = 42;
      class MyClass {}
    </script>

    <script>
      console.log(myLet); // Output: World
      console.log(myConst); // Output: 42
      console.log(MyClass); // Output: class MyClass {}

      console.log(window.myLet); // Output: undefined
      console.log(window.myConst); // Output: undefined
      console.log(window.MyClass); // Output: undefined
    </script>
    </body>
    </html>
    ```

**Key Differences Summarized:**

* **Global Object Properties:**
    * `var` and `function`: Yes, they become properties of `window`.
    * `const`, `let`, and `class`: No, they do not become properties of `window`.
* **Access:**
    * `var` and `function`: Accessible via `window.variableName` or `window.functionName()`.
    * `const`, `let`, and `class`: Accessible directly by their names.
* **Scope:**
    * All are document scoped, meaning they are available to other scripts within the same HTML document.

**Why the Difference?**

* **Avoiding Global Pollution:** The newer behavior with `const`, `let`, and `class` helps to prevent "global pollution," which is when too many variables and functions are added to the global object. This can lead to naming conflicts and make code harder to maintain.
* **Block Scoping:** `const` and `let` have block scope (within curly braces `{}`), which is a more modern and predictable scoping behavior. While at the top level of a script they are document scoped, they do not act like the older var declarations.

**In essence:**

While all top-level declarations in non-module scripts are shared within the document, only `var` and `function` declarations become properties of the global `window` object. `const`, `let`, and `class` declarations are scoped to the document but not to the global object, leading to cleaner and more predictable code.
