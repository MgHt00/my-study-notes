# Using the enumerable attribute with arrays [^1]

Arrays in JavaScript are objects, so you can define properties on them using Object.defineProperty().

    let arr = [1, 2, 3, 4, 5];

    // Make the element at index 1 and index 3 non-enumerable
    Object.defineProperty(arr, '1', {
      enumerable: false
    });
    
    Object.defineProperty(arr, '3', {
      enumerable: false
    });
    
    // Using for...in loop
    for (let index in arr) {
      console.log(index);  // Output: "0", "2", "4"
    }
    
    // Using Object.keys()
    console.log(Object.keys(arr));  // Output: ["0", "2", "4"]
    
    // The elements at index 1 and index 3 are still accessible directly
    console.log(arr[1]);  // Output: 2
    console.log(arr[3]);  // Output: 4
    
    // Using forEach (it will still visit all elements)
    arr.forEach((value, index) => {
      console.log(index, value);  // Output: 0 1, 1 2, 2 3, 3 4, 4 5
    });

#### Explanation
1. Define Array: Create an array arr with elements `[1, 2, 3, 4, 5]`.
2. Make Indices Non-Enumerable: Use Object.defineProperty() to set the enumerable attribute of elements at index `1` and index `3` to false.
3. Iterate with `for...in`:
  - Only the indices `0`, `2`, and `4` are logged since indices `1` and `3` are non-enumerable.
4. Get Own Properties with Object.keys():
  - `Object.keys(arr)` returns `["0", "2", "4"]`, excluding the non-enumerable indices `1` and `3`.
5. Access Directly:
  - The elements at indices `1` and `3` are still accessible directly.
6. Using forEach:
  - Note that `Array.prototype.forEach()` will still visit all elements in the array, including non-enumerable ones.

### Methods Affected by enumerable Attribute
- Affected: `for...in`, `Object.keys()`, `Object.entries()`, `Object.getOwnPropertyNames()`.
- Not Affected: Standard `for` loops, `Array.prototype.forEach()`, `Array.prototype.map()`, `Array.prototype.filter()`, `Array.prototype.reduce()`, and other array methods that access elements directly.

### Method Using forEach
      let result = [];
      arr.forEach((value, index) => {
        if (arr.propertyIsEnumerable(index)) {
          result.push(value);
        }
      });
      
      console.log(result);  // Output: [1, 3, 5]

### Alternate Method [^2]

    let arr = [1, 2, 3, 4, 5];

    // Make the element at index 1 and index 3 non-enumerable
    Object.defineProperty(arr, '1', {
      enumerable: false
    });
    
    Object.defineProperty(arr, '3', {
      enumerable: false
    });
    
    // Using Object.entries() to filter and map only enumerable properties
    let filteredArray = Object.entries(arr)
      .filter(([index, value]) => arr.propertyIsEnumerable(index))
      .map(([index, value]) => value);
    
    console.log(filteredArray);  // Output: [1, 3, 5]

1. Define Array: Create an array arr with elements `[1, 2, 3, 4, 5]`.
2. Make Indices Non-Enumerable: Use `Object.defineProperty()` to set the enumerable attribute of elements at index `1` and index `3` to false.
3. `Object.entries()`: Convert the array into an array of key-value pairs (entries), where each entry is an array `[index, value]`.
4. Filter: Use `filter()` to only keep the entries where the property is enumerable. The propertyIsEnumerable method checks if a property is enumerable.
5. Map: Use `map()` to extract the values from the filtered entries.

[^1]: ChatGPT ရဲ့ အကူညီနဲ့ ရထားတဲ့ code ပါ.
[^2]: မစမ်းသပ်ရသေးပါ။
