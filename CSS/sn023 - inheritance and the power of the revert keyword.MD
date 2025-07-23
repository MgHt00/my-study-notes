You've hit on a very common point of confusion with the `revert` keyword, especially how it interacts with inheritance\! Your initial understanding that `revert` resets to user-agent styles isn't entirely wrong, but the authors' statement adds a crucial nuance that makes both perspectives correct in different scenarios.

Let's break down `revert` and where your understanding and the authors' statement align:

### The `revert` Keyword's Core Purpose

`revert` resets the cascaded value of a property to the value established by the **previous cascade origin** for that specific property.

The cascade origins, in increasing order of precedence, are:

1.  **User Agent styles** (browser defaults, e.g., `<a>` tags are blue and underlined)
2.  **User styles** (styles applied by the user via browser extensions or accessibility settings)
3.  **Author styles** (your CSS)
4.  **`!important` styles** (from any of the above, but still following an order of precedence)

When you use `revert` in your **Author styles**, you're telling the browser: "Ignore any value I (the author) set for this property on this element. Instead, use whatever value would have been applied from a **User style** or, failing that, from the **User Agent (browser default) style**."

### The Nuance: `revert` and Inherited vs. Non-Inherited Properties

This is where the distinction between "parent's value" and "user-agent style" comes into play:

1.  **For INHERITED Properties (like `color`, `font-size`, `text-align`, `line-height`):**

      * The **user-agent stylesheet** often **doesn't explicitly set a value** for these properties on every element. Instead, their default behavior is to **inherit** from their parent.
      * When you use `revert` on an inherited property, you're telling the browser: "Strip away my author-defined value, and go back to what the user-agent or user stylesheet would have done."
      * For inherited properties, what the user-agent or user stylesheet would have done is **allow it to inherit from its parent (if the parent has a value)**.
      * **Therefore, the authors are correct:** For inherited properties, `revert` will indeed make the property take the value of its parent (if the parent has a value), because that's often the effective "user-agent" or "user" default behavior.

    **Example:**

    ```html
    <div style="color: blue;">
      <p style="color: red; /* Author style */">
        Hello
        <span style="color: revert;">World</span> </p>
    </div>
    ```

    Here, `color: revert;` on the `<span>` means "go back to what the browser would normally do for color." The browser's normal behavior for `color` is to inherit, so it inherits `blue` from the `<div>` via the `p`.

2.  **For NON-INHERITED Properties (like `border`, `background`, `padding`, `width`, `height`):**

      * These properties **do not inherit** from their parent by default.
      * When you use `revert` on a non-inherited property, you're still telling the browser: "Strip away my author-defined value, and go back to what the user-agent or user stylesheet would have done."
      * Since these properties don't inherit, the "user-agent" default is usually an explicit initial value for that property (e.g., `border: none;`, `background: transparent;`).
      * **Therefore, your understanding is correct here:** For non-inherited properties, `revert` will typically reset them to the user-agent's default (initial) value for that property.

    **Example:**

    ```html
    <div style="border: 2px solid blue;">
      <p style="border: 5px dashed red; /* Author style */">
        Some text <span style="border: revert;"></span> </p>
    </div>
    ```

    Here, `border: revert;` on the `<span>` means "go back to what the browser would normally do for border." The browser's normal behavior for `border` on a `<span>` is `none`, not to inherit from the parent.

### Conclusion

You haven't misunderstood; you've just encountered the nuance\!

  * **Your thought (`revert` resets to user-agent styles) is fundamentally correct.**
  * The **authors' statement clarifies *how* that user-agent reset often manifests for *inherited properties***, which is by allowing them to inherit from the parent, as that's usually the user-agent's default behavior for such properties.

`revert` is incredibly useful for creating isolated components where you want to explicitly strip away the "global" or "site-wide" author styles for specific properties, allowing you to build up a fresh set of styles without fighting the cascade.

[G]
