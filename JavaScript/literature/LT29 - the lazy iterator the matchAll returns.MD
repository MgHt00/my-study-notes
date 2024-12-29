The `matchAll()` method in JavaScript returns a **lazy iterator**, specifically an **iterator of match objects**. This iterator conforms to the ECMAScript Iterable protocol, which means you can use it with constructs like `for...of` loops or the spread operator (`...`) to iterate over all matches.

Each item in the iterator is an array-like object representing a match, similar to the result of `RegExp.prototype.exec()`:

1. **The first element of each array** is the full match.
2. **Subsequent elements** contain the matches for capturing groups (if any).
3. The match object also includes the properties:
   - `index`: The position of the match in the string.
   - `input`: The original string.
   - `groups`: An object containing named capturing groups (if defined in the regex).

---

### Example of `matchAll()`

#### Code
```javascript
const regex = /(\w+)-(\d+)/g;
const str = "Item-123 and Product-456 are on sale.";

const matches = str.matchAll(regex);

// Using a for...of loop to iterate
for (const match of matches) {
  console.log(match);
}

// Alternative: Converting to an array
const matchesArray = [...str.matchAll(regex)];
console.log(matchesArray);
```

#### Output
Each `match` object looks like this:
```javascript
[
  "Item-123",      // Full match
  "Item",          // Captured group 1
  "123",           // Captured group 2
  index: 0,        // Position of the match
  input: "Item-123 and Product-456 are on sale.",
  groups: undefined // Named groups, if any
]
[
  "Product-456",
  "Product",
  "456",
  index: 14,
  input: "Item-123 and Product-456 are on sale.",
  groups: undefined
]
```

---

### Key Characteristics of the Iterator
1. **Lazy Evaluation**: Matches are calculated as you iterate through the results, not all at once. This is memory efficient, especially for large strings.
2. **Reusable**: You can iterate over the results multiple times by re-invoking `matchAll()`.

### Comparison to Other Iterators
- Similar to the iterators returned by `Map.prototype.entries()` or `Set.prototype.values()`.
- Unlike arrays, the results aren't stored in memory upfront but are generated on-demand during iteration.

For more information, see the [MDN Web Docs on `matchAll()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/matchAll).
