Yes, the `async` keyword can be used with various types of function declarations in JavaScript. The key takeaway is that an `async` function always returns a `Promise`.

-----

### 1\. `async` with a Function Statement

This is the most common way to declare an asynchronous function.

```javascript
// Function Statement
async function fetchData() {
  const response = await fetch('https://api.example.com/data');
  const data = await response.json();
  return data;
}
```

-----

### 2\. `async` with a Function Expression

You can assign an `async` function to a variable.

```javascript
// Function Expression
const getData = async function() {
  const response = await fetch('https://api.example.com/data');
  const data = await response.json();
  return data;
};
```

-----

### 3\. `async` with an Arrow Function

This is a popular and concise way to define asynchronous functions.

```javascript
// Arrow Function
const getMoreData = async () => {
  const response = await fetch('https://api.example.com/more-data');
  const data = await response.json();
  return data;
};
```

-----

### 4\. `async` with Object Literal Methods

You can define an `async` method directly inside an object literal.

```javascript
// Object Literal Method
const service = {
  data: 'initial data',
  async fetchData() { // The method shortcut form
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    this.data = data;
    return this.data;
  }
};
```

-----

### 5\. `async` with Class Methods

The `async` keyword is also used to define methods within a class.

```javascript
// Class Method
class DataFetcher {
  async fetchData() {
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    return data;
  }
}
```

---

Yes, you are exactly right. With both function expressions and object literal methods, you call the asynchronous function using the variable or object property it's assigned to, just like you would with any other function.

### 1\. Function Expression

For a function expression, you call the assigned variable followed by parentheses, like `getData()`.

```javascript
const getData = async function() {
  // ...
};

// Calling the async function expression
getData().then(data => {
  console.log('Received data:', data);
});
```

### 2\. Object Literal Method

For an object literal method, you use dot notation to access the method on the object, like `service.fetchData()`.

```javascript
const service = {
  async fetchData() {
    // ...
  }
};

// Calling the async object method
service.fetchData().then(data => {
  console.log('Received data:', data);
});
```

This consistency is one of the main benefits of `async/await`. It allows you to use familiar syntax (`()`, `.`) to call functions that behave asynchronously and return promises.
