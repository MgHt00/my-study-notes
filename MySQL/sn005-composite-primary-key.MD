That is an extremely sharp observation! At first glance, it definitely looks like a bug or a contradiction of the "one primary key" rule. However, what you are seeing is a very specific database concept called a **Composite Primary Key**.

The rule still holds: a table can only have **one** Primary Key. The "trick" here is that a single Primary Key can be made up of **multiple columns** working together as a team.

---

## 👥 What is a Composite Primary Key?

In the command you ran, you didn't create two separate primary keys. Instead, you created one single "Super Key" that uses two columns (`language_id` AND `name`) to define uniqueness.

Think of it like a **First Name** and a **Last Name**:

* Many people are named "John."
* Many people are named "Smith."
* But there is only one "John Smith" in your specific circle.

By grouping `language_id` and `name` together, MySQL ensures that the **combination** of those two values is never repeated in the table.

---

## 🛠️ Why would you do this?

In the `language` table, `language_id` is already unique (1, 2, 3...). Adding `name` to the key might seem redundant, but authors often use this example to teach you how to handle "Relationship Tables."

Imagine a table called `film_actor` that links actors to movies.

* An actor can be in many movies.
* A movie can have many actors.
* To prevent someone from accidentally listing the same actor in the same movie twice, you create a Composite Primary Key: `PRIMARY KEY (actor_id, film_id)`.

---

## 🔍 How to see the "Teamwork"

If you run `DESC language;` now, you will see something interesting in the "Key" column. Both `language_id` and `name` will have the label **PRI**.

This does **not** mean they are two keys. It means "This column is *part of* the Primary Key."

### The "Rules" of the Composite Key:

1. **Uniqueness:** You can have `(1, 'English')` and `(2, 'English')`. That's allowed because the *combination* is different.
2. **No Nulls:** Because they are part of the Primary Key, **neither** column is allowed to be empty (`NULL`).
3. **One Key:** If you tried to run `ALTER TABLE language ADD PRIMARY KEY (some_other_column);` now, MySQL would throw an error saying "Multiple primary key defined."

---
[G]
