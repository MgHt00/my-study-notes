Let's break down what the authors are explaining about generator functions.

### Generator Functions and Iterable Iterators

1. **Generator Function Definition**: A generator function is defined using the `function*` syntax. It's different from regular functions because it can pause and resume its execution.

2. **Not Immediate Execution**: When you call a generator function, it does not execute its body immediately. Instead, it returns a special kind of object known as an **iterable iterator**.

3. **Iterable Iterator**: This object has a `next()` method, which controls the execution of the generator. When you call `next()`, the generator function starts running until it hits a `yield` expression.

4. **Yield and Next**: The `yield` expression pauses the function, and the `next()` method returns the value provided by `yield`. Each subsequent call to `next()` resumes the function from where it was paused, continuing until the next `yield` or the end of the function.

### Example:

```javascript
function* myGenerator() {
  yield 1;
  yield 2;
  yield 3;
}

const iterator = myGenerator(); // Returns an iterable iterator object

console.log(iterator.next()); // { value: 1, done: false }
console.log(iterator.next()); // { value: 2, done: false }
console.log(iterator.next()); // { value: 3, done: false }
console.log(iterator.next()); // { value: undefined, done: true }
```

- **First Call (`myGenerator()`)**: This does not run the code inside `myGenerator`. Instead, it returns an iterator.
- **Subsequent `next()` Calls**: Each `next()` call runs the generator up to the next `yield`, pausing execution and returning the yielded value.
  
So, the "chunks" referred to by the authors are the sections of code between the `yield` statements in the generator function. Each call to `next()` runs the next chunk until it reaches the next `yield`. This allows for lazy evaluation, computing values only when needed, which can be very efficient for certain use cases.

Would you like more examples or further clarification on any part of this?
