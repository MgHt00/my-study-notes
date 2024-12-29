Certainly! The statement compares the behavior of a **non-global regular expression** (without the `g` flag) when used with `String.prototype.match()` versus `RegExp.prototype.exec()`. Both methods return the same result under these conditions.

Here's how they work:

### Using `match()`
When a non-global regex is passed to `String.prototype.match()`, it:
1. Finds the first match in the string.
2. Returns an array with:
   - The full match in the first element.
   - Any capturing groups in subsequent elements.
3. Includes `index`, `input`, and `groups` properties.

### Using `exec()`
When the same regex is passed to `RegExp.prototype.exec()`:
1. Finds the first match in the string.
2. Returns the same type of array as `match()` under these conditions, with:
   - The full match.
   - Capturing groups.
   - `index`, `input`, and `groups` properties.

---

### Example Code

#### Shared Regex
```javascript
const regex = /(\w+)-(\d+)/; // Match a word, a dash, and a number
const str = "Item-123 is on sale.";
```

#### Using `match()`
```javascript
const matchResult = str.match(regex);
console.log(matchResult);
// Output:
// [
//   "Item-123",
//   "Item",
//   "123",
//   index: 0,
//   input: "Item-123 is on sale.",
//   groups: undefined
// ]
```

#### Using `exec()`
```javascript
const execResult = regex.exec(str);
console.log(execResult);
// Output:
// [
//   "Item-123",
//   "Item",
//   "123",
//   index: 0,
//   input: "Item-123 is on sale.",
//   groups: undefined
// ]
```

---

### Key Observations
- Both methods produce identical arrays when the regex is non-global.
- The returned array contains the match and any capturing groups, as well as `index`, `input`, and `groups`.

### Why They Differ for Global Regexes
If the `g` flag is used, `match()` returns **all matches** as an array of strings, while `exec()` can be called repeatedly to process each match separately.
