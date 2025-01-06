### JSON `toJSON()`, Reviver, and Replacer Functions

#### 1. **`toJSON()` Method:**
The `toJSON()` method allows you to define how an object should be converted into JSON when passed to `JSON.stringify()`. When you call `JSON.stringify()` on an object, if the object has a `toJSON()` method, this method is called, and its return value is used as the JSON representation of the object.

**Example:**
```javascript
const user = {
  firstName: "John",
  lastName: "Doe",
  age: 30,
  toJSON() {
    return { fullName: `${this.firstName} ${this.lastName}` };
  }
};

console.log(JSON.stringify(user)); // Output: {"fullName":"John Doe"}
```

#### 2. **Replacer Function:**
The replacer function is an optional parameter of `JSON.stringify()`. It allows you to modify the behavior of the stringification process. The replacer function is called for each property of the object being stringified and can modify the output or exclude properties.

**Syntax:**
```javascript
JSON.stringify(value, replacer)
```

**Example:**
```javascript
const user = {
  firstName: "John",
  lastName: "Doe",
  age: 30
};

const replacer = (key, value) => {
  // Exclude age property
  if (key === "age") return undefined;
  return value;
};

console.log(JSON.stringify(user, replacer)); // Output: {"firstName":"John","lastName":"Doe"}
```

#### 3. **Reviver Function:**
The reviver function is an optional parameter of `JSON.parse()`. It allows you to transform the values before returning them during the parsing process. The reviver function is called for each property in the object being parsed and can modify the resulting object.

**Syntax:**
```javascript
JSON.parse(text, reviver)
```

**Example:**
```javascript
const jsonString = '{"firstName":"John","lastName":"Doe","age":30}';

const reviver = (key, value) => {
  // Combine firstName and lastName into a fullName property
  if (key === "firstName") return undefined;
  if (key === "lastName") return undefined;
  return value;
};

const user = JSON.parse(jsonString, reviver);
console.log(user); // Output: {age: 30}
```

---

#### Use Cases and Practical Examples:

- **`toJSON()`**: Custom serialization logic for an object, e.g., excluding sensitive information before sending data to a client.
- **Replacer Function**: Filter out or transform specific properties during serialization.
- **Reviver Function**: Modify or validate data when parsing JSON, e.g., converting date strings to `Date` objects.

These features provide fine control over JSON serialization and parsing processes, making them powerful tools for managing data interchange. Let me know if you'd like to explore specific scenarios further!
