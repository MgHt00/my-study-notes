Yes, in JavaScript, you can import one JavaScript file into another, similar to how you import a CSS file into another CSS file. There are a few ways to achieve this depending on the environment you're working in. Here are the two most common methods:

### 1. **Using `<script>` tags (for client-side JavaScript in HTML)**

You can include one JavaScript file in another by simply adding multiple `<script>` tags in your HTML file, ensuring that the files are loaded in the correct order. For example:

```html
<!-- Load the first script -->
<script src="file1.js"></script>

<!-- Load the second script which can use functions or variables from the first -->
<script src="file2.js"></script>
```

In this approach, `file2.js` can access everything from `file1.js` as long as `file1.js` is loaded first.

### 2. **Using `import`/`export` (for modern JavaScript with ES Modules)**

If you're working with modern JavaScript (ES6+), you can use the `import` and `export` statements to import one JavaScript file into another. To use this method, your files should have either a `.mjs` extension or you should use `type="module"` in your `<script>` tag.

Here’s an example:

#### In `file1.js`:
```javascript
// Export a function from file1.js
export function greet(name) {
  return `Hello, ${name}!`;
}
```

#### In `file2.js`:
```javascript
// Import the greet function from file1.js
import { greet } from './file1.js';

console.log(greet('Alice'));  // Output: Hello, Alice!
```

#### In HTML:
```html
<script type="module" src="file2.js"></script>
```

This approach allows you to modularize your code, making it more reusable and maintainable.

### Summary:
- **Using `<script>` tags** is simple for non-module JavaScript, and the scripts are executed in the order they're loaded.
- **Using `import/export`** is recommended for modular JavaScript, making your code cleaner and easier to manage.

Let me know if you need help with anything specific!

---

Yes, you can use the `export` keyword with a **JavaScript class**, but you would use `export class` rather than `export function`. The `export` keyword works the same way for both functions and classes. Here's how you can export a class in JavaScript:

### Example with a class:

```javascript
// Exporting a class using export
export class Global {
  constructor() {
    this.name = "Global Object";
  }

  greet() {
    return `Hello from ${this.name}`;
  }
}
```

### How to import and use it in another file:

```javascript
// Importing the class in another file
import { Global } from './Global.js';

const globalInstance = new Global();
console.log(globalInstance.greet()); // Output: Hello from Global Object
```

### Explanation:
- The `export` keyword before the class definition makes the `Global` class available for import in other modules.
- You can use `import { Global } from './Global.js'` to bring in the class and create instances of it in your other JavaScript files.

### Using Default Export (optional):
If you want to export just one class (or function) as the default export, you can do this:

```javascript
// Default export for the class
export default class Global {
  constructor() {
    this.name = "Global Object";
  }

  greet() {
    return `Hello from ${this.name}`;
  }
}
```

And import it like this:

```javascript
// Importing the default exported class
import Global from './Global.js';

const globalInstance = new Global();
console.log(globalInstance.greet()); // Output: Hello from Global Object
```

### Summary:
- Use `export class ClassName {}` to export a class.
- Use `import { ClassName } from './filename'` to import it in other files.
- Optionally, you can use `export default class ClassName {}` if the class is the only export of the module.

Let me know if you need further clarification!
