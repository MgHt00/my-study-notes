Yes, you understand it correctly!  

The initial `p = Promise.resolve(undefined);` creates a resolved Promise, ensuring that `.then()` can be chained immediately in the loop.  

### Step-by-step breakdown:
1. `Promise.resolve(undefined)` ensures that the first `.then()` inside the loop executes immediately.
2. Inside the loop, each `fetchOne(url)` returns a Promise, and `.then(() => fetchOne(url))` ensures that each request starts only after the previous one completes.
3. `p` is reassigned in each iteration to chain the next `then()`, ensuring sequential execution.
4. Finally, `.then(() => bodies)` ensures that when all fetches complete, the function resolves with `bodies`.

This approach enforces sequential execution instead of running all fetch requests in parallel.
