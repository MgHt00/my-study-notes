The author states in one point that "It is critical to understand right away that the `await` keyword does not cause your program to block and literally do nothing until the specified Promise settles. The code remains asynchronous, and the `await` simply disguises this fact. This means that any code that uses await is itself asynchronous."

And in another point:

```
let value1 = await getJSON(url1);

let value2 = await getJSON(url2);
```

The problem with this code is that it is unnecessarily sequential. the fetch of the second URL will not begin until the first fetch is complete."

For me that 2 statements contradict each other, one states "do not cause your program to block" and the other states "the second function will not begin until the first fetch is complete". Can you explain it to me?

---

[G] You've identified a subtle but important point about how `await` interacts with asynchronous operations. Let's break it down:

**Key Concepts:**

* **Asynchronous Nature of `await`:**

   - While `await` makes asynchronous code *appear* synchronous, it doesn't actually block the main thread of execution. 
   - The code *continues* to execute after the `await` expression, but the execution of the subsequent code is *dependent* on the resolution of the Promise.

* **Sequential Execution within a Single `async` Function:**

   - Within a single `async` function, `await` expressions *do* cause sequential execution. 
   - The code following an `await` expression will not execute until the Promise associated with that `await` has resolved.

**Explanation of the Apparent Contradiction:**

* **"await does not cause your program to block"**: This refers to the fact that the entire program doesn't come to a complete standstill while waiting for a Promise to resolve. Other parts of the program can continue to execute concurrently.

* **"the second fetch will not begin until the first fetch is complete"**: This refers to the *sequential* nature of `await` *within the same `async` function*. 

   - If you have two `await` expressions in a row within the same `async` function, the second `await` will only execute *after* the first `await` has resolved.

**Analogy:**

Imagine you're at a restaurant. 

* **Asynchronous Nature:** You can order your food and continue talking to your friends while you wait for it to be prepared. The restaurant's kitchen doesn't stop everything else while they cook your meal.

* **Sequential Execution within a Single Order:** You can't eat your main course before you've finished your appetizer. You must wait for the appetizer to arrive and consume it before the main course is served.

**How to Achieve Concurrency:**

To fetch `url1` and `url2` concurrently, you can use techniques like:

* **`Promise.all()`:**

   ```javascript
   const [value1, value2] = await Promise.all([getJSON(url1), getJSON(url2)]); 
   ```

   - `Promise.all()` allows you to wait for multiple Promises to resolve simultaneously.
   - The `await` expression in this case will wait for *all* Promises in the array to resolve before proceeding.

* **Separate `async` Functions:**

   - Create separate `async` functions for each fetch operation.
   - These functions can then be executed concurrently (e.g., using `Promise.all()` or other concurrency techniques).

I hope this explanation clarifies the apparent contradiction and helps you understand how `await` interacts with asynchronous operations!
