[G] Yes, let's illustrate how to use `window.onunhandledrejection` or `window.addEventListener("unhandledrejection", ...)` to catch unhandled Promise rejections.

**Example Using `window.onunhandledrejection`:**

```html
<!DOCTYPE html>
<html>
<head>
  <title>Unhandled Promise Rejection</title>
</head>
<body>
  <h1>Unhandled Promise Rejection Example</h1>

  <button onclick="createRejectedPromise()">Create Rejected Promise</button>

  <script>
    window.onunhandledrejection = function(event) {
      console.error("Unhandled Promise Rejection:");
      console.error("Reason:", event.reason);
      console.error("Promise:", event.promise);

      alert("An unhandled Promise rejection occurred. Check the console for details.");

      // Prevent default browser behavior (optional):
      // event.preventDefault();
    };

    function createRejectedPromise() {
      new Promise((resolve, reject) => {
        reject(new Error("Promise rejected!"));
      });
      // No .catch() is attached to this promise.
    }
  </script>
</body>
</html>
```

**Example Using `window.addEventListener("unhandledrejection", ...)`:**

```html
<!DOCTYPE html>
<html>
<head>
  <title>Unhandled Promise Rejection</title>
</head>
<body>
  <h1>Unhandled Promise Rejection Example</h1>

  <button onclick="createRejectedPromise()">Create Rejected Promise</button>

  <script>
    window.addEventListener("unhandledrejection", function(event) {
      console.error("Unhandled Promise Rejection:");
      console.error("Reason:", event.reason);
      console.error("Promise:", event.promise);

      alert("An unhandled Promise rejection occurred. Check the console for details.");

      // Prevent default browser behavior (optional):
      // event.preventDefault();
    });

    function createRejectedPromise() {
      new Promise((resolve, reject) => {
        reject(new Error("Promise rejected!"));
      });
      // No .catch() is attached to this promise.
    }
  </script>
</body>
</html>
```

**Explanation:**

1.  **`window.onunhandledrejection = function(event) { ... }` or `window.addEventListener("unhandledrejection", function(event) { ... })`:**
    * These lines set up a handler for unhandled Promise rejections.
    * The handler function receives an `event` object.

2.  **`event` Object:**
    * `event.reason`: The reason for the rejection (usually an `Error` object).
    * `event.promise`: The Promise object that was rejected.

3.  **Error Handling Logic:**
    * Inside the handler function, you can:
        * Log the rejection details to the console.
        * Display an error message to the user.
        * Send the error details to a server.
        * Perform other error handling actions.

4.  **`event.preventDefault()` (Optional):**
    * Calling `event.preventDefault()` prevents the default browser behavior, which might include logging a warning to the console.

5.  **`createRejectedPromise()` Function:**
    * This function creates a new Promise that is immediately rejected.
    * No `.catch()` handler is attached to the Promise, so the rejection becomes unhandled.

**How it Works:**

1.  When you click the "Create Rejected Promise" button, the `createRejectedPromise()` function is called.
2.  A new Promise is created and rejected.
3.  Because there is no `.catch()` handler, the rejection becomes unhandled.
4.  The browser invokes the `window.onunhandledrejection` or the event listener registered for "unhandledrejection" events.
5.  The handler function logs the rejection details to the console and displays an alert.

**Important Notes:**

* This handler is a last-resort measure. It's best to use `.catch()` blocks to handle Promise rejections in specific parts of your code.
* `window.onunhandledrejection` and `addEventListener` offer similar functionality; `addEventListener` is generally preferred for its flexibility (allowing multiple handlers).
* Just like the onerror handler, in a production environment, you will want to send the error information to a logging service.
