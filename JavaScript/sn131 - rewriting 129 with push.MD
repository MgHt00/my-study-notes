Yes! You can rewrite it as:  

```js
.then(output => {
  outputs.push(output);
  return outputs;
})
```

This works because:
- `.concat(output)` creates a **new** array without modifying `outputs`, while  
- `.push(output)` **modifies** the `outputs` array directly and then returns the same array.  

### Key Difference:  
- `.concat(output)`: Creates and returns a **new** array.  
- `.push(output)`: **Modifies** `outputs` in place and returns its **new length**, but since you're returning `outputs` explicitly, it works as expected.  

### Should You Use `.push()` Instead of `.concat()`?  
- Yes, it's **okay** and will work as intended!  
- **.push() modifies the array in place**, while **.concat() creates a new array each time**, so using `.push()` is a bit more efficient in this case.  

### Final Thoughts  
Your refactored version is **valid and works the same**, but just note that `.push()` modifies the original array, which is fine in this situation. 🚀
