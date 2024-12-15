Absolutely! The `match()` function in JavaScript behaves differently depending on whether the regular expression has the `g` (global) flag. Without the `g` flag, `match()` returns an array where the first element is the full match and the subsequent elements are the text matched by any **capturing groups** (parenthesized parts of the regex).

Here are some examples to illustrate this:

---

### Example 1: No `g` flag, capturing groups

```javascript
const str = "My age is 25";
const regex = /age is (\d+)/;

const result = str.match(regex);

console.log(result);
```

#### Output:
```
[
  'age is 25', // Full match
  '25'         // Captured group (the number inside the parentheses)
]
```

- **`result[0]`** contains the entire match `"age is 25"`.
- **`result[1]`** contains the part matched by the capturing group `(\d+)`, which captures the digits.

---

### Example 2: Multiple capturing groups, no `g` flag

```javascript
const str = "Hello, John Doe!";
const regex = /Hello, (\w+) (\w+)!/;

const result = str.match(regex);

console.log(result);
```

#### Output:
```
[
  'Hello, John Doe!', // Full match
  'John',             // First capturing group: (\w+)
  'Doe'               // Second capturing group: (\w+)
]
```

- **`result[0]`** contains the full match `"Hello, John Doe!"`.
- **`result[1]`** contains the first capturing group `"John"`.
- **`result[2]`** contains the second capturing group `"Doe"`.

---

### Explanation

- The `match()` function returns:
  - The full matched string in **index 0**.
  - The substrings that match each **capturing group** in subsequent indices.

- **Without the `g` flag**, `match()` only returns the first match it finds along with any captured groups. It doesn't search for multiple matches.

Let me know if you need further clarification! 😊
