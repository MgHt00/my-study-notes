Great question! Let’s break it down step by step to clarify how `handleNextInput` gets an empty array as a parameter.

### 1️⃣ The Key Part: `Promise.resolve([]).then(handleNextInput)`

At the end of `promiseSequence()`, we have this line:

```js
return Promise.resolve([]).then(handleNextInput);
```

Here’s what happens:
- `Promise.resolve([])` creates a resolved Promise with an **empty array (`[]`)** as its value.
- `.then(handleNextInput)` means that `handleNextInput` will be called with the resolved value of the Promise, which is `[]`.

So, `handleNextInput([])` is effectively called **with an empty array** as its first argument.

---

### 2️⃣ What Happens in `handleNextInput`?

The function `handleNextInput` is defined as:

```js
function handleNextInput(outputs) {
  if (inputs.length === 0) {
    return outputs;
  } else {
    let nextInput = inputs.shift();
    return promiseMaker(nextInput)
      .then(output => outputs.concat(output))
      .then(handleNextInput);
  }
}
```

- The first time `handleNextInput` runs, `outputs` is `[]` (from `Promise.resolve([])`).
- If `inputs.length === 0`, the function simply **returns `outputs`**, ending the process.
- Otherwise:
  1. The next item is **shifted** from `inputs` and passed to `promiseMaker`.
  2. The resulting Promise resolves to a value (`output`).
  3. That value is **concatenated** to `outputs` (creating a new array).
  4. The process repeats by calling `handleNextInput(newOutputs)`.

---

### 3️⃣ Summary
- `Promise.resolve([])` **initializes `outputs` as an empty array** and passes it to `handleNextInput`.
- Each time `handleNextInput` is called, it processes one input and adds the result to `outputs`.
- The recursion continues until there are no more inputs left.
