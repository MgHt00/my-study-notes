You're absolutely on the right track! The "nonflexed main-axis size" that the authors are referring to is essentially synonymous with what we just discussed as the "preflexed size."

It represents the size of a flex item **before** the Flexbox algorithm starts distributing extra space or shrinking items.

And yes, an explicit declaration of `width` (if `flex-direction` is `row` or `row-reverse`) or `height` (if `flex-direction` is `column` or `column-reverse`) can indeed be that "nonflexed main-axis size" in a very common scenario.

Let's elaborate:

1.  **Main Axis:**
    * If `flex-direction: row` or `row-reverse`, the main axis is horizontal, and the main-axis size is the **width**.
    * If `flex-direction: column` or `column-reverse`, the main axis is vertical, and the main-axis size is the **height**.

2.  **"Nonflexed" / "Preflexed" Size and `flex-basis`:**
    The property that primarily determines this "nonflexed main-axis size" is `flex-basis`.

    * **If `flex-basis` is set to a specific length (e.g., `flex-basis: 150px;`):**
        Then `150px` is the "nonflexed main-axis size." In this case, `flex-basis` *overrides* any explicit `width` or `height` property you might have set on the item for the purpose of the initial flex calculation.

    * **If `flex-basis: auto;` (this is the default):**
        This is where your observation comes into play. When `flex-basis` is `auto`, the "nonflexed main-axis size" is determined by the item's `width` (if main axis is horizontal) or `height` (if main axis is vertical), or its content's intrinsic size if no `width`/`height` is explicitly set.

**So, to answer your question directly:**

Yes, an explicit `width` (or `height` depending on `flex-direction`) declaration *can be* the "nonflexed main-axis size" **if and only if `flex-basis` is set to `auto` (its default value).**

If `flex-basis` is set to a fixed value (like `100px` or `50%`), then that `flex-basis` value is the "nonflexed main-axis size," and any `width`/`height` declaration will be ignored for the initial flex calculation (though it might still affect how the content renders *within* the final flex item size).

The authors are likely using "nonflexed main-axis size" as a more general term for the initial size of the item *before* it grows or shrinks to fit the container. `flex-basis` is the CSS property that dictates this size.

[G]
