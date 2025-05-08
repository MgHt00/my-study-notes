[G] That's an interesting point the authors make about the universal selector (`*`) and inheritance. Let's break down what they mean by "short-circuiting inheritance."

In CSS, inheritance is a powerful mechanism where certain properties applied to a parent element are passed down (inherited) to its child elements. For example, if you set the `color` or `font-family` on the `<body>` element, all the text within the body will usually inherit those styles unless they are overridden by more specific rules.

The universal selector (`*`) matches *every* element on the page. When you apply styles using the universal selector, you are directly targeting each and every element. This direct targeting can interfere with the normal flow of inheritance in a couple of key ways:

**1. Overriding Inherited Values:**

If you set a property using the universal selector, it will apply that value to all elements, potentially overriding a value that would have been inherited from an ancestor.

**Example:**

```html
<body>
  <div style="color: blue;">
    <p>This text should be blue.</p>
  </div>
</body>

<style>
  * {
    color: black; /* Universal selector sets color to black for all elements */
  }
</style>
```

In this case, even though the `<div>` has `color: blue;` applied directly, the more specific rule for the `<div>` will win due to CSS specificity rules. However, the `<p>` element would normally *inherit* the `color: blue` from its parent `<div>`. But because the universal selector also targets the `<p>` and sets its `color` to `black`, the inheritance of `blue` is effectively "short-circuited." The `<p>` will be black.

**2. Preventing Default Inherited Values:**

Some CSS properties are inherited by default (like `color`, `font-family`, `font-size`, `text-align`, etc.). If you set a different value for these inherited properties using the universal selector, you prevent the elements from receiving their initial inherited values from their parents.

**Example:**

```html
<body>
  <p>This text would normally inherit the body's font.</p>
</body>

<style>
  body {
    font-family: sans-serif;
  }

  * {
    font-family: serif; /* Universal selector sets a different font for all */
  }
</style>
```

Here, the `<p>` element would normally inherit `font-family: sans-serif` from the `<body>`. However, the universal selector sets `font-family: serif` on the `<p>` directly, thus short-circuiting the expected inheritance.

**Why is this important?**

Overusing the universal selector with broad, resetting styles can make your CSS more verbose and harder to manage. You might end up having to write more specific rules later to re-establish the styles you intended to be inherited.

**Modern CSS Practices:**

Modern CSS often favors more targeted resets or normalizations (like using libraries like Normalize.css) that address browser inconsistencies without aggressively overriding all inherited properties. This allows for a more predictable and manageable inheritance flow.

**In summary, when the authors say the universal selector can "short-circuit inheritance," they mean that by applying styles directly to every element, it can prevent elements from inheriting styles from their ancestors, either by overriding the inherited value or by setting a different initial value.**

Does this explanation clarify the concept for you?
