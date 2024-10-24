## `arguemnts` Object
The `arguments` object is an array-like object available with functions.  It contains all the arguments passed to the function.
```javascript
  function example () {
    console.log(arguments); // {'0': 'a', '1': 'b', '2': 'c', length: 3}
    console.log(arguments.length); // 3
    console.log(arguments[0]); //  'a'
}

example('a','b','c');
```
