[^1]In JavaScript, a shallow copy of an array creates a new array containing references to the same elements as the original array. This means that if the elements of the array are objects or arrays, the references to those objects or arrays are copied, not the objects themselves. Consequently, changes to the objects or arrays inside the copied array will affect the original array and vice versa.

# Shallow Copy

## Creating a Shallow CopyShallow Copy

#### 1. Using slice():

    let original = [1, 2, 3];
    let shallowCopy = original.slice();

#### 2. Using concat():
    let original = [1, 2, 3];
    let shallowCopy = [].concat(original);

#### 3. Using the spread operator (...):
    let original = [1, 2, 3];
    let shallowCopy = [...original];

### Example with Objects

    let original = [{ a: 1 }, { b: 2 }];
    let shallowCopy = original.slice();

    shallowCopy[0].a = 42;
    
    console.log(original[0].a); // Output: 42
    
In the example above, modifying an object inside the shallowCopy also affects the original array because both arrays hold references to the same objects.

# Deep Copy
A deep copy of an array creates a new array with completely new instances of the objects or arrays contained in the original array. This means that the new array and the original array do not share any references; changes to one will not affect the other.

## Creating a Deep Copy
#### Using JSON.parse and JSON.stringify:

    let original = [{ a: 1 }, { b: 2 }];
    let deepCopy = JSON.parse(JSON.stringify(original));
    
    deepCopy[0].a = 42;
    
    console.log(original[0].a); // Output: 1
    
#### Using a Recursive Function:

    function deepCopy(obj) {
        if (obj === null || typeof obj !== 'object') {
            return obj;
        }
    
        if (Array.isArray(obj)) {
            let copy = [];
            for (let i = 0; i < obj.length; i++) {
                copy[i] = deepCopy(obj[i]);
            }
            return copy;
        }
    
        let copy = {};
        for (let key in obj) {
            if (obj.hasOwnProperty(key)) {
                copy[key] = deepCopy(obj[key]);
            }
        }
        return copy;
    }
    
    let original = [{ a: 1 }, { b: 2 }];
    let deepCopyArr = deepCopy(original);
    
    deepCopyArr[0].a = 42;
    
    console.log(original[0].a); // Output: 1
    
## Key Differences
### Shallow Copy:

-Only the references to the elements are copied.
-Changes to objects or arrays within the copied array affect the original array.

### Deep Copy:

-Creates new instances of objects or arrays within the copied array.
-Changes to objects or arrays within the copied array do not affect the original array.

## Summary
-Shallow Copy: Copies only the first level of elements, which includes references to objects or other arrays. Methods include slice(), concat(), and the spread operator (...).
-Deep Copy: Copies all levels, ensuring no references to the original elements are retained. Methods include JSON.parse(JSON.stringify()) and custom recursive functions.
-Understanding the difference between shallow and deep copies is crucial when working with arrays and objects in JavaScript to ensure the desired behavior in your programs.

---

<i>But the author states as follows :

    The spread operator is a convenient way to create a (shallow) copy of an array:
    let original = [1,2,3];
    let copy = [...original];
    copy[0] = 0; // Modifying the copy does not change the original
    original[0] //=> 1
</i>

The author is correct in stating that using the spread operator creates a shallow copy of an array. However, the provided example demonstrates modifying primitive values (like numbers), which do not share references in a shallow copy. Let's clarify this with detailed explanations and examples:

### Shallow Copy with Primitive Values
When working with arrays of primitive values (e.g., numbers, strings, booleans), a shallow copy behaves as expected because primitive values are copied by value, not by reference.

#### Example with Primitive Values
    let original = [1, 2, 3];
    let copy = [...original];
    
    // Modifying the copy
    copy[0] = 0;
    
    console.log(copy[0]); // Output: 0
    console.log(original[0]); // Output: 1
In this case, changing copy[0] does not affect original[0] because each element in the array is a primitive value, and primitives are copied by value.

### Shallow Copy with Objects or Arrays
When working with arrays of objects or arrays, a shallow copy means that the copied array contains references to the same objects or arrays as the original. Therefore, changes to the objects or arrays within the copied array will affect the original array.

#### Example with Objects
    let original = [{ a: 1 }, { b: 2 }];
    let copy = [...original];
    
    // Modifying an object within the copy
    copy[0].a = 42;
    
    console.log(copy[0].a); // Output: 42
    console.log(original[0].a); // Output: 42 (changes in copy affect the original)

### Summary
-Primitive Values: When you create a shallow copy of an array of primitives using the spread operator (...), modifications to the copied array do not affect the original array because primitives are copied by value.
-Objects/Arrays: When you create a shallow copy of an array of objects or arrays, the copied array contains references to the same objects or arrays as the original. Modifications to these objects or arrays in the copied array will affect the original array because objects and arrays are copied by reference.

### Conclusion
The spread operator (...) creates a shallow copy of an array. When dealing with primitive values, this shallow copy behaves like a deep copy because primitives are copied by value. However, when dealing with objects or arrays, the shallow copy contains references to the same objects or arrays, meaning changes to these nested structures in the copied array will reflect in the original array.

[^1]: ဒီ note က [JavaScript: The Definitive Guide, 7th Edition by David Flanagan](https://www.oreilly.com/library/view/javascript-the-definitive/9781491952016/) စာအုပ်မှာပါတဲ့ အကြောင်းအရာကို ChatGPT နဲ့ ပြန်အမေးအဖြလုပ်ထားတာ ဖြစ်ပါတယ်။
