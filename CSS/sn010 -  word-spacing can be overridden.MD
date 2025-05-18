That's a slightly nuanced statement by the authors, and your interpretation points to a common area of confusion. Let's clarify how `word-spacing` interacts with `text-align`.

You **absolutely can** set the `word-spacing` property when `text-align` is set to `left` or `right`. The `word-spacing` property will affect the spacing between words as you would expect in those alignments.

**The authors' statement about `word-spacing` being overridden in justified text (`text-align: justify;`) refers to a specific behavior that is *inherent to the justification process itself*.**

Here's the breakdown:

* **`text-align: left;` and `text-align: right;`**: When text is aligned to the left or right, the browser primarily adjusts the trailing spaces (on the right for `left`, on the left for `right`) to make each line end appropriately. The spaces *between* the words generally remain at their natural width, plus any additional spacing you define with `word-spacing`.

* **`text-align: justify;`**: Justification aims to make each line of text (except possibly the last) fill the entire width of its containing block. To achieve this, the browser **distributes the extra space among the spaces between words**. This means the browser will *modify* the natural word spaces, effectively overriding or augmenting the `word-spacing` you might have set.

**In other words:**

* With `text-align: left;` or `right;`, the `word-spacing` you set is generally respected and added to the normal inter-word spaces.
* With `text-align: justify;`, while your `word-spacing` might provide a *starting point* for the inter-word spaces, the browser will then adjust these spaces (making some wider than others, if necessary) to achieve the full line width. The final visual word spacing might not be exactly what you set with `word-spacing` because of this justification process.

**Analogy:**

Imagine you have a row of words (like people standing in a line).

* If you tell them to align to the left or right, you might also tell them to stand a certain distance apart (`word-spacing`). They will generally maintain that distance.
* If you tell them to "justify" and fill a specific width of a room, they will still try to maintain a certain distance, but they might also need to spread out unevenly to reach both walls. The initial distance you set is still a factor, but the "justification" requirement takes precedence in the distribution of the extra space.

Therefore, you can certainly use `word-spacing` with `text-align: left;` or `right;` to control the spacing between words. The authors' comment is specifically about how the justification algorithm in `text-align: justify;` can alter the effect of `word-spacing`.

--

You've picked up on another important distinction between `word-spacing` and `letter-spacing`! The authors are highlighting that once you set `letter-spacing` to a specific length value (like `1px`, `0.5em`, etc.), that spacing between individual letters will generally **not** be overridden by the `text-align: justify;` property in the same way that `word-spacing` can be.

Here's why:

* **`word-spacing` affects the spaces *between* words.** When text is justified, the browser has the flexibility to adjust these inter-word spaces (making some wider than others) to make the lines fill the available width.

* **`letter-spacing` affects the space *between* each individual character (letters, punctuation, etc.).** If the browser were to override a fixed `letter-spacing` to achieve justification, it would likely result in text that looks very distorted and unreadable, with inconsistent and unnatural gaps within words.

**The browser's priority with `text-align: justify;` is to adjust the inter-word spaces to fill the line.** It doesn't typically manipulate the spacing *within* words (controlled by `letter-spacing` when set to a length) to achieve this.

**Think of it this way:**

Imagine the letters in a word are tightly linked. `letter-spacing` lets you put a consistent gap between these linked units. When justifying text, the browser can stretch the gaps *between* these groups of linked letters (the words) but generally won't try to pull apart the individual links *within* the words.

**Therefore, if you set `letter-spacing: 1px;`, you will have a 1-pixel space between each letter in the text, regardless of whether `text-align` is `left`, `right`, or `justify`. The justification algorithm will primarily work on the spaces between the words.**

**Important Note:**

While a length value for `letter-spacing` is generally not overridden by `text-align: justify;`, if `letter-spacing` is set to its initial value (`normal`), the browser *might* make very minor adjustments to letter spacing as part of sophisticated justification algorithms, especially in complex typography scenarios. However, a specific length value enforces a consistent space that the browser will typically respect.

**In summary, the authors are pointing out the robustness of `letter-spacing` (when set to a length) in maintaining consistent spacing between characters, even when text is justified. The justification process focuses on the more flexible inter-word spaces.**

[G] 
