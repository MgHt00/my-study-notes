You're right, `await` is typically used before a function call that returns a Promise, not directly on a Promise variable. Let's illustrate with examples:

**1. Using `await` with a Function Call:**

```javascript
async function fetchData() {
  const data = await fetch('https://api.example.com/data'); // await before the function call (fetch)
  const jsonData = await data.json(); 
  return jsonData;
}
```

In this example:

- `await fetch('https://api.example.com/data')`: This line waits for the `fetch()` function to resolve (return a Response object).
- `await data.json()`: This line waits for the `json()` method on the Response object to resolve and return the parsed JSON data.

**2. Using `await` with a Promise Variable (Less Common):**

```javascript
async function fetchData() {
  const fetchPromise = fetch('https://api.example.com/data'); 
  const data = await fetchPromise; // await used on the Promise variable
  const jsonData = await data.json(); 
  return jsonData;
}
```

While technically possible, using `await` directly on a Promise variable like `fetchPromise` is less common. It's generally more concise and readable to use `await` directly before the function call that returns the Promise.

**Key Points:**

- `await` is primarily used to pause the execution of an `async` function until a Promise resolves.
- It's most commonly used before a function call that returns a Promise.
- Using `await` directly on a Promise variable is possible but less common and often less readable.

I hope this clarifies the common usage patterns of `await` with Promises!
