The last sentence is saying that, in a constructor function, if you explicitly return an object, that object will be the result of calling the constructor, instead of the usual new object that is created automatically.

Here’s a breakdown:

1. **Normal behavior of constructor functions**:
   A constructor function creates a new object when it is called with the `new` keyword. It initializes that new object, and when the function reaches the end, it implicitly returns that new object.

   Example:

   ```js
   function Person(name) {
     this.name = name;  // 'this' refers to the new object being created
   }

   let p = new Person("Alice");  // Creates a new Person object
   console.log(p.name);  // Outputs "Alice"
   ```

   In this example, `new Person("Alice")` creates a new `Person` object and assigns `name = "Alice"` to it. When the function finishes, the new object is returned implicitly.

2. **When the constructor explicitly returns an object**:
   If the constructor function explicitly returns an object, that object will override the default behavior of returning the new instance. The returned object will be used instead.

   Example:

   ```js
   function Person(name) {
     this.name = name;
     return { customName: "Overridden" };  // Explicitly returning an object
   }

   let p = new Person("Alice");  
   console.log(p);  // Outputs { customName: "Overridden" }
   ```

   In this case, `new Person("Alice")` creates a new object, but because the constructor explicitly returns `{ customName: "Overridden" }`, the object that gets assigned to `p` is the returned object, not the automatically created `Person` object.

   **Important note**: If the constructor returns a *primitive value* (like a number, string, etc.), it will be ignored, and the new object will still be returned.

   Example:

   ```js
   function Person(name) {
     this.name = name;
     return 42;  // Returning a primitive value
   }

   let p = new Person("Alice");
   console.log(p);  // Outputs the new Person object, not 42
   ```

   In this case, the return statement is ignored because `42` is not an object. The `new` object that was created will be returned instead. 

In summary, if a constructor function explicitly returns an object, that object becomes the result of the constructor call. Otherwise, the new object created by `new` is returned implicitly.

---

```javascript
function Person(name) {
  this.name = name;  // 'this' refers to the new object being created
}

let p = new Person("Alice");  // Creates a new Person object
console.log(p.name);  // Outputs "Alice"

In this code I don't understand whether 'name' belongs to 'Person' or 'p'. 
```

---

In this code, the property `name` actually belongs to the newly created object `p`, not the `Person` function itself.

Here's how it works:

1. When `new Person("Alice")` is called, JavaScript creates a new object.
2. Inside the `Person` function, `this` refers to this newly created object, so `this.name = name;` assigns `"Alice"` to the `name` property of that new object.
3. The `Person` function then returns the new object, and `p` becomes a reference to it.

After this, the `name` property belongs to `p` (the instance), not to the `Person` function.

### To clarify:

- `p.name` is `"Alice"` because the `name` property belongs to the instance `p`.
- If you check `Person.name`, it will return `undefined` (or something unrelated), because `name` is not a property of the `Person` function itself.

In short, `name` is a property of each **instance** created by `Person`, not of `Person` itself.
