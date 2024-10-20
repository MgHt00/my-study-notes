## To close the gaps in a sparse array
```javascript
let dense = sparse.filter( () => ture);
```
An arrow function that takes not parameters and always returns `true`.

## To close gaps and remove `undefined` and `null` elements
```javascript
a = a.filter( x => x !== undefined && x !== null);
```
