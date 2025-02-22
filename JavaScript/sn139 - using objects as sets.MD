Yes! The author is referring to a clever way of using JavaScript objects as *sets* before `Set` was introduced in ES6.

---

### **Understanding the Statement**
> "Objects can be used (by ignoring the value part of the string-to-value mapping) to represent sets of strings."

This means we can use an object’s **keys** to store unique values, while ignoring their **values**.

---

### **Example: Using an Object as a Set**
Before ES6 introduced the `Set` object, developers used plain objects to represent sets. 

For example, if you wanted to keep track of unique words:
```javascript
const wordSet = {}; // Object as a "set"

// Add words (assign any value, we just care about the keys)
wordSet["apple"] = true;
wordSet["banana"] = true;
wordSet["cherry"] = true;

// Check if a word is in the set
console.log("apple" in wordSet);  // true
console.log("grape" in wordSet);  // false

// Remove a word
delete wordSet["banana"];

console.log(wordSet); // { apple: true, cherry: true }
```
- The **keys** of `wordSet` (`"apple"`, `"banana"`, `"cherry"`) act as set members.
- The **values** (`true`) are ignored—they could be anything.

---

### **Why is This Useful?**
1. **Ensures Uniqueness** – Objects do not allow duplicate keys, so using keys as set elements prevents duplicates.
2. **Fast Lookups** – Checking membership using `"key" in object` is efficient (`O(1)` time complexity).

---

### **ES6 `Set` vs. Object as a Set**
ES6 introduced the `Set` object, which is designed specifically for storing unique values:

```javascript
const wordSet = new Set();
wordSet.add("apple");
wordSet.add("banana");
wordSet.add("cherry");

console.log(wordSet.has("apple")); // true
console.log(wordSet.has("grape")); // false

wordSet.delete("banana");

console.log(wordSet); // Set { 'apple', 'cherry' }
```
✅ **`Set` is better** because:
- It allows **any** type of value, not just strings.
- It has built-in **methods** like `.has()`, `.add()`, `.delete()`.
- It is more **semantic** for set operations.

---

### **Summary**
| Feature          | Object as Set (`{}`) | `Set` (ES6) |
|----------------|----------------|---------|
| Uniqueness     | ✅ Yes | ✅ Yes |
| Lookup Speed   | ⚡ Fast (`"key" in obj`) | ⚡ Fast (`.has()`) |
| Supports Non-String Values | ❌ No (keys must be strings/symbols) | ✅ Yes (any value type) |
| Built-in Methods | ❌ No (`delete key`) | ✅ Yes (`.add()`, `.has()`, `.delete()`) |

Using an object as a set was a common trick in pre-ES6 JavaScript, but today, `Set` is the better choice. 
