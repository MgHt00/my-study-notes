You're absolutely correct! The behavior you're observing is consistent with how regex alternation works and matches. Let's break it down in the context of the example:

### Regex: `(ab|cd)+|ef`
- This expression matches:
  - `(ab|cd)+`: One or more occurrences of "ab" or "cd".
  - `|`: An alternation that checks "ef" if the left side doesn't match.
  - `ef`: Matches "ef" if `(ab|cd)+` fails.

### Input: `"acdef"`

When applying the regex:

1. The engine starts from the beginning of the string `"acdef"`.
2. **First Match Attempt**:
   - The group `(ab|cd)+` tries to match starting from the beginning:
     - It checks for "ab" and fails (the first character is "a").
     - It checks for "cd" and finds a match at index 2 (`"cd"`).
   - At this point, the `(ab|cd)+` group matches `"cd"`, and the engine stops looking further for more matches inside this group because it found a valid match.

3. **Alternation (`|ef`)**:
   - Since `(ab|cd)+` successfully matched `"cd"`, the right alternative `|ef` is ignored. This happens because the alternation is evaluated left-to-right, and a match on the left-hand side preempts any evaluation on the right-hand side.

4. **Result**:
   - The `match()` method only returns the match found by `(ab|cd)+`:
     - `["cd", undefined]` because the capturing group `(ab|cd)` matched `"cd"`, and there was no second match for `ef`.

### Why isn't `ef` matched?
This is what the authors mean by "the right alternative is ignored." The regex engine stops processing the alternation once it finds a valid match on the left (`(ab|cd)+`).

---

If you want to see matches for both `cd` and `ef` in the input, you would need to use a regex like this: `/((ab|cd)+|ef)/g`. This ensures that the engine continues to evaluate matches across the entire input.
