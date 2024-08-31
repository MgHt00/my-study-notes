You can use a commonly used method known as the Fisher-Yates (or Knuth) shuffle algorithm to shuffle an array.[^1] Here's a pre-built function for shuffling an array:

```javascript
function shuffleArray(array) {
  for (let i = array.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1));
    [array[i], array[j]] = [array[j], array[i]]; // Swap elements
  }
  return array;
}
```

### How It Works:
- The function iterates through the array from the last element to the first.
- For each element, it generates a random index and swaps the current element with the element at the random index.
- This ensures that every element has an equal probability of being placed in any position, resulting in a well-shuffled array.

### Usage Example:
```javascript
let arr = [1, 2, 3, 4, 5];
arr = shuffleArray(arr);
console.log(arr); // Output: A shuffled version of the array
```

You can use this `shuffleArray` function in your project whenever you need to shuffle your answer array or any other array.

[^1]: ChatGPT ဆီက ရထားတဲ့ code ပါ။ 