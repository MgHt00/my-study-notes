### How to copy EVERYTHING (Structure + Indexes)

**Step 1: Copy the "Blueprint"**
First, create an empty table that is a perfect structural clone:

```SQL
CREATE TABLE language_clone LIKE sakila.language;
```

This copies the indexes, primary keys, and auto-increment settings, but the table will be empty.

**Step 2: Move the "Furniture"**
Now, pour the data into that empty structure:

```SQL
INSERT INTO language_clone SELECT * FROM sakila.language;
```

#### To create a table and copy (without indexex)
```SQL
CREATE TABLE language_clone LIKE sakila.language;
```
---
