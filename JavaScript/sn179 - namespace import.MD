Yes, with the code `import * as stats from "./stats.js";`, you can access all of the named exports (functions, constants, objects, classes, etc.) from `stats.js` as properties of a single `stats` object.

This is known as a **namespace import** or **wildcard import**.

## How it Works

When you use `import * as name from "module";`, the JavaScript engine creates a single object (`stats` in this case) and populates it with every export from the source module (`stats.js`). The name of the property on the `stats` object will be the same as the name of the exported item.

-----

## Example

Let's say `stats.js` contains the following exports:

```javascript
// stats.js
export const PI = 3.14159;
export function sum(a, b) {
  return a + b;
}
export class MyStats {
  constructor() {
    this.value = 0;
  }
}
```

Now, in your other file, if you use `import * as stats from "./stats.js";`, you can access all these exports like this:

```javascript
// main.js
import * as stats from "./stats.js";

console.log(stats.PI);       // Accessing the PI constant
const total = stats.sum(5, 3); // Calling the sum function
console.log(total);          // Output: 8

const myStatsInstance = new stats.MyStats(); // Instantiating the MyStats class
console.log(myStatsInstance.value);          // Output: 0
```

## Advantage

The main advantage of this approach is that it avoids polluting the current module's scope with multiple imported names. All the imported items are neatly organized under a single namespace object, which can help prevent naming conflicts.

[G]
