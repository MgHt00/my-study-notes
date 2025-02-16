You're pointing out a subtle but important detail about the timing of Promise resolution/rejection with `Promise.resolve()` and `Promise.reject()`.

**Key Point:**

While `Promise.resolve()` and `Promise.reject()` *create* Promises that are "resolved" or "rejected" respectively, the actual resolution or rejection doesn't always happen *immediately* at the point where `Promise.resolve()` or `Promise.reject()` is called.

**Illustration:**

```javascript
function someFunction() {
  console.log("Before Promise.resolve()"); 
  const resolvedPromise = Promise.resolve("Success!"); 
  console.log("After Promise.resolve()"); 

  resolvedPromise.then(value => {
    console.log("Promise resolved with:", value); 
  });

  console.log("End of someFunction()"); 
}

someFunction(); 
```

**Output:**

```
Before Promise.resolve()
After Promise.resolve()
End of someFunction()
Promise resolved with: Success!
```

**Explanation:**

1. **`someFunction()`:** 
   - `console.log("Before Promise.resolve()")` is executed first.
   - `const resolvedPromise = Promise.resolve("Success!");` creates a Promise that is scheduled to resolve with the value "Success!". However, the resolution itself might not happen immediately.
   - `console.log("After Promise.resolve()")` is executed.
   - `console.log("End of someFunction()")` is executed.

2. **Promise Resolution:** 
   - After `someFunction()` completes, the JavaScript engine will eventually fulfill the `resolvedPromise` with the value "Success!". 
   - The `then()` callback will then be executed, and "Promise resolved with: Success!" will be logged to the console.

**In Summary:**

* `Promise.resolve()` and `Promise.reject()` create Promises that are scheduled to resolve or reject.
* The actual resolution or rejection usually happens **after** the current synchronous block of code (e.g., the `someFunction()` in the example) has finished executing.
* This allows the JavaScript engine to efficiently schedule and execute Promises.

I hope this illustration clarifies the timing of Promise resolution/rejection with `Promise.resolve()` and `Promise.reject()`!
