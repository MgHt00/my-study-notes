[G] You're right to ask! `concat()` is **not** a global method in JavaScript. 

* **`concat()`** is a method specifically for **String** objects. 

   - It's used to **combine** one or more strings to the end of the existing string.

* **Example:**

   ```javascript
   const str1 = "Hello, ";
   const str2 = "world!";
   const combined = str1.concat(str2); 
   console.log(combined); // Output: "Hello, world!"
   ```

* **Array.prototype.concat()**

   - There's also an `Array.prototype.concat()` method, which is used to **create a new array** by combining the elements of one or more arrays.

   - **Example:**

     ```javascript
     const array1 = [1, 2];
     const array2 = [3, 4];
     const combinedArray = array1.concat(array2); 
     console.log(combinedArray); // Output: [1, 2, 3, 4]
     ```

**In summary:**

* `concat()` itself is not a global function.
* It's a method that belongs to the `String` and `Array` prototypes, allowing you to concatenate strings or combine arrays.

I hope this clarifies the concept of `concat()`!
