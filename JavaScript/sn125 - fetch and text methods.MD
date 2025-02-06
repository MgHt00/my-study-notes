[G] * **`fetch()`** is a **global function** in JavaScript. It's not a method of a specific object. You can directly call it in your code:

   ```javascript
   fetch('https://api.example.com/data') 
     .then(response => response.json()) 
     .then(data => { 
       console.log(data); 
     });
   ```

* **`text()`** is a **method of the `Response` object**. 

   - The `fetch()` function returns a `Promise` that resolves with a `Response` object. 
   - The `Response` object represents the server's response to the HTTP request. 
   - You call the `text()` method on the `Response` object to extract the response body as plain text.

**Example:**

```javascript
fetch('https://example.com')
  .then(response => { 
    if (!response.ok) { 
      throw new Error('Network response was not ok'); 
    }
    return response.text(); 
  })
  .then(text => { 
    console.log(text); 
  })
  .catch(error => { 
    console.error('There has been a problem with your fetch operation:', error); 
  });
```

In this example:

1. `fetch('https://example.com')` initiates the request and returns a Promise.
2. The first `.then()` block checks if the response was successful (`response.ok`) and then calls `response.text()` to get the response as text.
3. The second `.then()` block receives the text data and logs it to the console.
4. The `.catch()` block handles any errors that might occur during the fetch operation.

I hope this clarifies the relationship between `fetch()` and `text()`!
