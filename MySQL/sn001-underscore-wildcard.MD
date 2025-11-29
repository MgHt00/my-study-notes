Just like the percent sign (`%`) is crucial for pattern matching, the underscore has a specific and important job in SQL filtering.

## 🕵️ Understanding the Underscore Wildcard (`_`)

The underscore (`_`) wildcard is used in a `LIKE` pattern to represent **any single character**.

In contrast, the percent sign (`%`) represents **zero or more** of any character.

### Your Query Explained

Let's break down the filter in your query: `WHERE actors LIKE 'NAT_%'`

* **`NAT`**: This part is matched literally. The string must start with the letters N, A, and T, in that order.
* **`_` (Underscore)**: This matches exactly **one** character.
* **`%` (Percent Sign)**: This matches **zero or more** characters.

**Combined Meaning:** The pattern `'NAT_%'` is looking for any actor's name that starts with **"NAT"**, followed by **one single character**, and then followed by **any number of other characters**.

### 📝 Example of What It Matches

| Actor Name | Match? | Why? |
| :--- | :--- | :--- |
| **NAT H**ART | Yes | NAT, followed by the single space character (` `), then H, A, R, T. |
| **NATALIE** WALLEN | Yes | NAT, followed by the single letter **A**, then L, I, E, etc. |
| **NAT P**ORTMAN | Yes | NAT, followed by the single space character (` `), then P, O, R, T, M, A, N. |
| **NATHAN** JOE | Yes | NAT, followed by the single letter **H**, then A, N, etc. |
| **NAT** | No | Fails because it's not followed by at least one character. |

### 💡 Why Use the Underscore?

The main reason to use `_` is to enforce **length constraints** in your search pattern:

1.  **Fixed Length:** If you only want to find four-letter words, you would use four underscores: `WHERE word LIKE '____'`
2.  **Specific Position:** If you want to find names where the second letter is 'A' but the first and third can be anything, you use: `WHERE name LIKE '_A_'`

In your case, using `'NAT_%'` is a very precise way to ensure that "NAT" is part of the name, followed by at least one other character, which is often used to ensure you get full names, initials, or to distinguish prefixes.

---

**Would you like to write a query using the underscore to find all actors whose first name is exactly four letters long and starts with 'J'?**
