The `:not()` pseudo-class has a special rule for specificity: **it adds zero specificity to the selector itself.**

Instead, the specificity of a `:not()` selector is determined by the **most specific selector(s) contained within its parentheses**.

Here's how it works with a few examples:

* **`div:not(.my-class)`**
    * The `:not()` part adds nothing.
    * The specificity is calculated from `div` (type selector = 1) and `.my-class` (class selector = 1).
    * Specificity: **0,1,1**

* **`:not(#my-id)`**
    * The `:not()` part adds nothing.
    * The specificity comes from `#my-id` (ID selector = 1).
    * Specificity: **1,0,0**

* **`#main :not(p)`**
    * The `#main` part has a specificity of `1,0,0`.
    * The `:not(p)` part adds zero specificity for `:not()` itself, plus the `p` (type selector = 1).
    * The combined specificity is calculated as if the selector were `#main p`, which is **1,0,1**.

This rule is what makes `:not()` so useful. It allows you to create exclusions without unintentionally inflating the specificity of your CSS rules. It's also why you can't use it to increase a selector's power.

[G]
