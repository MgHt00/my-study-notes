You've hit on a common point of confusion with `font-size-adjust`\! It's not about directly setting the size of the font you apply the property to, but rather about setting a **reference point** for any *other* fonts that might be used as fallbacks or overrides.

Let's break it down:

### What `font-size-adjust` Does

`font-size-adjust` aims to address the problem that different fonts, even when set to the exact same `font-size` (e.g., `10px`), can appear to be significantly different in their perceived size. This is largely due to variations in their **x-height** (the height of a lowercase 'x' relative to the overall font size).

  * **`font-size-adjust` tells the browser: "For this element, my ideal or primary font has an x-height ratio of [this value]. If you end up using a different font (a fallback or override), please scale it so its x-height matches what my primary font's x-height would have been."**

### Analyzing the Author's Example

  * **Verdana:** Has a relatively **large x-height** compared to its overall font size. Its x-height ratio is `0.58`.
  * **Times:** Has a relatively **small x-height** compared to its overall font size. Its x-height ratio is `0.46`.

Now, let's look at the code:

```css
p {
  font: 10px Verdana, sans-serif; /* Primary font is Verdana, base size 10px */
  font-size-adjust: 0.58;          /* Set to Verdana's x-height ratio */
}

p.cl2 {
  font-family: Times, serif;       /* This paragraph specifically requests Times */
}
```

**Here's why `font-size-adjust: 0.58;` is set on the `p` (which initially uses Verdana):**

1.  **Setting the Reference:** By setting `font-size-adjust: 0.58;` on the `p` element (where Verdana is the primary font), you're establishing `0.58` as the **target x-height ratio** for *any font displayed in that paragraph*. This target is based on Verdana's characteristics.

      * At `10px` font-size, Verdana's x-height would be `10px * 0.58 = 5.8px`.

2.  **How it affects `p.cl2` (which uses Times):**

      * The `p.cl2` element **inherits** the `font-size-adjust: 0.58;` property from the general `p` rule.
      * When the browser renders `p.cl2` using `Times` (which has an x-height ratio of `0.46`), it knows the *target x-height* is `5.8px` (from `10px * 0.58`).
      * To make Times's x-height `5.8px`, the browser calculates the necessary `font-size` for Times:
        `Adjusted FontSize = Desired X-height / Times's X-height Ratio`
        `Adjusted FontSize = 5.8px / 0.46 ≈ 12.6px`

    So, even though `p.cl2` is declared with a `font-size` of `10px` (inherited from `p`), the browser will actually render `Times` at approximately `12.6px` in `p.cl2` to make its lowercase characters appear visually similar in height to 10px Verdana.

### Why not set `font-size-adjust` to `0.46` on Times?

If you were to set `font-size-adjust: 0.46;` (Times's ratio) on the `p` element instead, you would be saying: "My ideal font (Verdana) should have an x-height of 0.46 relative to its size." This would essentially try to shrink Verdana down to match Times's smaller x-height, which is generally not the goal. The goal is usually to make smaller x-height fonts appear as large as the primary, larger x-height font.

**In essence:**

You set `font-size-adjust` to the x-height ratio of your **primary, desired, or most legible font**. Then, any *other* font that gets rendered on that element (whether due to fallback or override) will be scaled *relative to that primary font's x-height* to maintain visual consistency in perceived size.

[G]
