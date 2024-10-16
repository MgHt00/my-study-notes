In JavaScript, *object shorthand properties* allow you to create objects with properties that directly use variable names as both the key and value. This shorthand can make code more concise and readable, especially when creating objects with values from existing variables. Here’s how it works with some examples:

### 1. Basic Shorthand Example
When a variable name matches the desired property name, you can use the shorthand syntax:

```javascript
let name = "Alice";
let age = 25;

// Without shorthand
let person = { name: name, age: age };

// With shorthand
let personShorthand = { name, age };
console.log(personShorthand); // { name: "Alice", age: 25 }
```

### 2. Shorthand with Function Properties
You can also use shorthand to define methods within an object:

```javascript
let dog = {
  breed: "Labrador",
  
  // Without shorthand
  bark: function() { 
    return "Woof!"; 
  },

  // With shorthand
  fetch() {
    return "Fetching...";
  }
};

console.log(dog.bark()); // "Woof!"
console.log(dog.fetch()); // "Fetching..."
```

### 3. Shorthand in Dynamic Object Creation
Object shorthand is useful when creating objects in functions or using dynamically generated values:

```javascript
function createUser(username, email) {
  return {
    username,
    email,
    createdAt: new Date(),
  };
}

console.log(createUser("johndoe", "johndoe@example.com"));
// { username: "johndoe", email: "johndoe@example.com", createdAt: current date }
```

### 4. Shorthand with Computed Properties
You can combine shorthand with computed property names:

```javascript
let key = "role";
let value = "admin";

let user = {
  name: "Jane",
  [key]: value, // Computed property name with shorthand
};

console.log(user); // { name: "Jane", role: "admin" }
```

### 5. Nested Object with Shorthand
Shorthand also works well in nested objects:

```javascript
let firstName = "John";
let lastName = "Doe";
let city = "New York";

let userInfo = {
  name: { firstName, lastName },
  location: { city },
};

console.log(userInfo); 
// { name: { firstName: "John", lastName: "Doe" }, location: { city: "New York" } }
```

### Summary

Object shorthand properties make your code cleaner, especially when creating objects with matching variable names, and help to reduce redundancy.
