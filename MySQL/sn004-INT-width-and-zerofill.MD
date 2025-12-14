They are primarily used for formatting how the numbers are *displayed*, rather than how they are stored.

---

##1. The 'Width' Parameter (Display Width)The 'width' parameter is the number you see in parentheses after an integer data type, such as `INT(11)` or `SMALLINT(5)`.

###📌 What It Is* **Syntax:** `INT(M)`, where M is the display width.
* **Purpose:** The width parameter M is a **non-functional hint** to the client program (like the MySQL CLI or a graphical tool) about how many characters wide the display column should be.
* **Does NOT Affect Storage:** Crucially, the display width **does not limit the range of values** that can be stored in the column. An `INT(3)` can still store the number 2,000,000,000 because the range is determined by the `INT` type itself (and whether it is `SIGNED` or `UNSIGNED`), not the width parameter.
* *Example:* Both `INT(5)` and `INT(11)` can store the exact same range of numbers, from -2,147,483,648 to 2,147,483,647.



###💡 Why It ExistsThe main reason to use the display width is for the next feature: **`ZEROFILL`**. If `ZEROFILL` is not used, the width parameter is typically ignored by the server and most modern client programs.

---

##2. The `ZEROFILL` AttributeThe `ZEROFILL` attribute is what makes the display width useful, as it changes how the numbers are padded for display.

###📌 What It Is* **Syntax:** `INT(M) ZEROFILL`
* **Purpose:** When `ZEROFILL` is specified, MySQL will automatically **left-pad** any number stored in that column with leading zeros until it reaches the specified display width (M).

###💡 Practical ExampleIf you define a column as `INT(5) ZEROFILL` and insert the value \mathbf{42}:

| Value Stored | Display Width (M) | Displayed Output |
| --- | --- | --- |
| 42 | 5 | 00042 |

If you insert the value \mathbf{123456}:

| Value Stored | Display Width (M) | Displayed Output |
| --- | --- | --- |
| 123456 | 5 | 123456 |

**Important Note:** If the number you insert is *wider* than M (like 123456 is wider than 5), the number is displayed fully. The display width only sets the **minimum** width for zero padding.

###⚠️ A Side Effect of `ZEROFILL`When you use the `ZEROFILL` attribute on an integer column, MySQL **automatically applies the `UNSIGNED` attribute** to that column, even if you did not explicitly specify `UNSIGNED`.

* This means the column can only store zero and positive numbers (it cannot store negative values). The negative sign (-) would conflict with the leading zeros.

[G]
