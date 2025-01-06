The statement means that when using a reviver function with `JSON.parse()`, this function is called for each key-value pair in the JSON string, but only for the primitive values (strings, numbers, booleans, `null`). It is not called for the objects or arrays themselves; instead, it's called for the elements inside them.

Here’s a breakdown of what this entails:

1. **Primitive Values**: The reviver function processes each primitive value in the JSON. For example, if the JSON string contains `"name": "John"`, the reviver function will be invoked with `"name"` as the key and `"John"` as the value.

2. **Objects and Arrays**: The reviver function doesn't process the entire objects or arrays directly. Instead, it processes each property of an object or each element of an array as a separate primitive value.

**Example to Illustrate:**
```javascript
const jsonString = '{"name": "John", "age": 30, "address": {"city": "New York"}}';

const reviver = (key, value) => {
  console.log(`Key: ${key}, Value: ${value}`);
  return value;
};

JSON.parse(jsonString, reviver);
```

**Output:**
```
Key: name, Value: John
Key: age, Value: 30
Key: city, Value: New York
Key: address, Value: [object Object]
Key: , Value: [object Object]
```

- Notice that `"city": "New York"` is processed separately from the `"address"` object.
- The top-level object is also passed to the reviver with an empty string (`""`) as the key after all its properties have been processed.

The reviver can thus be used to transform primitive values or even reconstruct specific data structures during parsing, offering granular control over the parsing process. 

Would you like to see an example where the reviver transforms specific values?
