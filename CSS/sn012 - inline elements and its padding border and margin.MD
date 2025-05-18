You're on the right track with your thinking about collapsing, but the behavior of padding, borders, and margins on **non-replaced inline elements** is a bit more specific than simple collapsing in the block-level sense.

Here's a breakdown of what the authors mean and how it differs from block-level margin collapsing:

**Vertical Effects on Non-Replaced Inline Elements:**

  * **Vertical Padding:** Top and bottom `padding` on a non-replaced inline element **will increase the total height of the element's inline box**, but it will do so visually by overlapping with the content above and below it on adjacent lines. It does *not* push away the lines above or below.

  * **Vertical Borders:** Similarly, top and bottom `border` on a non-replaced inline element **will also increase the total height of the element's inline box** and will visually overlap adjacent lines. It does *not* affect the line height or push other inline boxes vertically.

  * **Vertical Margins:** Top and bottom `margin` on a non-replaced inline element have **no effect** on the vertical layout or the height of the line box. They are essentially ignored in the vertical direction.

**Why is this different from block-level collapsing?**

Block-level margin collapsing occurs between the top and bottom margins of adjacent block-level boxes. The larger of the adjacent margins takes effect, and the smaller one is effectively "collapsed." This helps create more predictable vertical spacing between block elements.

Inline elements, however, are designed to flow within a line of text. Their vertical padding, borders, and margins are treated differently to maintain this flow:

  * **Maintaining Line Flow:** If vertical padding or margins on inline elements were to push away the lines above and below, it would disrupt the horizontal flow of the text and make inline layout very difficult to manage.

  * **Visual Overlap:** Instead, the visual expansion caused by vertical padding and borders is allowed to overlap with the line boxes above and below. The `line-height` property of the parent block element is the primary factor that determines the vertical spacing between lines of text.

**Illustration:**

```html
<p>This line has a <span style="padding-top: 20px; padding-bottom: 20px; border-top: 2px solid red; border-bottom: 2px solid blue; margin-top: 10px; margin-bottom: 10px; background-color: yellow;">tall inline</span> element.</p>
```

In this example:

  * The `<span>` will appear with 20px of padding above and below its text, and red and blue borders. These will likely overlap the lines of text above and below.
  * The top and bottom margins of 10px on the `<span>` will have **no visual effect** on the vertical spacing of the lines. The line containing "tall inline" will not be pushed down or further away from the surrounding lines due to these margins.

**In summary, the top and bottom padding and borders on non-replaced inline elements do not collapse in the block-level sense. Instead, they visually expand the inline box and can overlap adjacent lines. The top and bottom margins on non-replaced inline elements have no effect on the vertical layout.**

The authors are emphasizing that inline elements primarily affect the horizontal flow and the height of the line box is determined by the tallest/shortest inline content, not by the vertical formatting properties applied to individual inline elements.

-- 

That's a very astute visual interpretation of the behavior we just discussed, and the answer is **yes, that's exactly right\!**

Because the top and bottom padding and borders on the non-replaced inline `<span>` element increase its visual height without affecting the line box of the surrounding `<p>` element in a way that pushes the lines apart, the background color of the `<span>` will indeed likely **show through the text of the lines above and below it**.

Here's why:

1.  **The `<span>`'s inline box expands vertically due to the padding and borders.** It becomes taller than the normal line height of the text.

2.  **The surrounding lines in the `<p>` element maintain their normal line height.** They are not pushed further apart by the vertical padding and borders of the inline `<span>`.

3.  **Visual Overlap:** As a result, the expanded visual area of the `<span>` (including its background color, padding, and borders) will extend into the vertical space occupied by the line box of the line above and the line box of the line below, potentially overlapping the text in those adjacent lines.

**Think of it like this:** Imagine the lines of text are stacked with a certain vertical spacing (determined by `line-height`). The inline `<span>` is trying to visually grow taller within its line. Since it can't push the other lines away, it has to grow "into" the space of those adjacent lines.

**Example Visual Representation:**

```
This line of text is above the
+-------------------------------------+
|   tall inline                       |  <-- Yellow background, red/blue borders, padding
+-------------------------------------+
element and this line is below.
```

In a browser rendering, the yellow background and the red/blue borders of "tall inline" would likely visually overlap the "above" and "below" lines of text if the padding is significant enough relative to the `line-height`.

This behavior is a key characteristic of how inline elements with vertical padding and borders are rendered and is different from how block-level elements with padding and margins affect vertical spacing.

Your ability to visualize this overlap demonstrates a good understanding of the concept\!

[G]
