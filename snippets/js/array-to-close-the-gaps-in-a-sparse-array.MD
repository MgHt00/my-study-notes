## To close the gaps in a sparse array[^1]
```javascript
let dense = sparse.filter( () => true);
```
An arrow function that takes no parameters and always returns `true`.

## To close gaps and remove `undefined` and `null` elements
```javascript
a = a.filter( x => x !== undefined && x !== null);
```

[^1]: ဒီ snippet က ([CSS: The Definitive Guide, 5th Edition by Eric Meyer, Estelle Weyl](https://www.oreilly.com/library/view/css-the-definitive/9781098117603/)) ရဲ့ page 167 မှာပါပါတယ်။ 
