## Merge Array of Objects into A Single Object

```javascript
let objects = [
  { name: "Alice", age: 25 },
  { location: "New York" },
  { occupation: "Engineer" }
];
let mergedObject = objects.reduce((accumulator, currentValue) => Object.assign(accumulator, currentValue), {});
console.log(mergedObject); 
// Output: { name: 'Alice', age: 25, location: 'New York', occupation: 'Engineer' }
```

```javascript
const objArray = [
  { a: 1, b: 2 },
  { b: 3, c: 4 },
  { d: 5 }
];

const mergedObj = objArray.reduce((acc, currentObj) => {
  return { ...acc, ...currentObj };
}, {});

console.log(mergedObj);  // { a: 1, b: 3, c: 4, d: 5 }
```
