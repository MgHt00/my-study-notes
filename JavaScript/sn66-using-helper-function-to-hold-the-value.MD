**Snippet A**
```javascript
function constfunc(v) {
  return () => v;
}

let funcs = [];
for (var i = 0; i < 10; i++) {
  funcs[i] = constfunc(i);
}

funcs[5](); // This will return 5
```

**Snippet B**
```javascript
function constfuncs() {
let funcs = [];
for (var i = 0; i < 10; i++) {
funcs[i] = () => i;
}
return funcs;
}

funcs[5](); // This will return 10
```

I understand var is function scope but I don't get it right when it comes with the closure.  Can you teach me why snippet B returns 10 when snippet A returns 5 by breaking down the code?  

---

Sure, I can break this down for you!

This is a common example of how closures interact with variables declared with `var` and how those variables are bound to the closure.

### Snippet A

In **Snippet A**, we use a helper function `constfunc(v)` to create a closure with a variable `v` that is specific to each loop iteration.

Here’s how it works:

1. The `for` loop runs from `i = 0` to `i = 9`.
2. In each iteration, `constfunc(i)` is called.
   - `constfunc(i)` returns a new function that *closes over* the value of `v` at the time it was called.
   - This means each returned function remembers the specific value of `v` when `constfunc(i)` was called.
3. Each function returned by `constfunc(i)` is stored in `funcs[i]`.
4. When `funcs[5]()` is called, it invokes the function that was created in the 5th iteration with `v = 5`, so it returns `5`.

This works because `v` is *captured by value* in each call to `constfunc(i)`, so each `funcs[i]` has its own unique value of `v`.

### Snippet B

In **Snippet B**, there’s no helper function to capture the value of `i`. Instead, each function stored in `funcs[i]` directly references the variable `i` from the enclosing `for` loop.

Here's how it unfolds:

1. The `for` loop runs from `i = 0` to `i = 9`.
2. In each iteration, the arrow function `() => i` is added to `funcs[i]`.
   - This function doesn’t have its own local `i`; it refers to the `i` declared with `var` in the `for` loop.
   - Since `var` has function scope, the `i` in each function references the *same* variable, not a unique one for each function.
3. After the loop finishes, `i` is now `10` (the loop ends when `i` reaches 10).
4. When `funcs[5]()` is called, it looks at `i`, which is `10` at that point, so it returns `10`.

In this case, every function in `funcs` array references the *same* variable `i`, and that variable’s final value is `10`.

### Key Differences

- **Snippet A**: Each function has its own copy of `v`, so each one "remembers" the value of `i` at the time it was created.
- **Snippet B**: All functions reference the same `i` variable. By the time the functions are called, `i` is `10`.

### Fixing Snippet B

To make Snippet B behave like Snippet A, you could wrap the function creation in an IIFE (Immediately Invoked Function Expression):

```javascript
function constfuncs() {
  let funcs = [];
  for (var i = 0; i < 10; i++) {
    funcs[i] = ((v) => () => v)(i); // IIFE captures `i` by value
  }
  return funcs;
}

const funcs = constfuncs();
console.log(funcs[5]()); // Outputs 5
```

In this revised code, the IIFE `((v) => () => v)(i)` creates a new function with a unique `v` for each iteration, capturing the current value of `i` each time, so `funcs[5]()` will return `5` as expected.
