Sure! Let's break down what the authors mean with an example using destructuring assignment and an iterator.

### Example:

```javascript
// Define an iterable object
const iterable = {
  data: [1, 2, 3, 4, 5],
  [Symbol.iterator]() {
    let index = 0;
    return {
      next: () => {
        if (index < this.data.length) {
          return { value: this.data[index++], done: false };
        } else {
          return { done: true };
        }
      }
    };
  }
};

// Destructuring assignment with an iterator
const [first, second] = iterable;

console.log(first);  // Output: 1
console.log(second); // Output: 2
```

### Explanation:
1. **Iterable Object**: The object `iterable` has a custom iterator defined with `[Symbol.iterator]`, which returns an iterator object.
2. **Destructuring Assignment**: The line `const [first, second] = iterable;` uses destructuring to extract the first two values from the `iterable`.
3. **`next()` Calls**: The `next()` method is called just twice to get the values for `first` and `second`.
4. **Ignored Values**: Even though `iterable` could provide more values (3, 4, 5), they are never requested because the destructuring assignment only needs two values.

### What Happens Under the Hood:
- The destructuring assignment `[first, second]` causes the iterator's `next()` method to be called twice.
- The first call retrieves the first value (1), and the second call retrieves the second value (2).
- After getting the necessary values, the iterator is not used further, so the remaining values (3, 4, 5) are not fetched.

This illustrates how destructuring assignment with iterators works by only consuming as many values as needed, leaving any additional values unrequested.
