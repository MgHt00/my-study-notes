## 🔢 Understanding Hierarchical Sorting

SQL sorts data using a **left-to-right hierarchy**. It applies the first sorting rule, and only if two rows are identical based on that rule, does it move on to the second rule.

### 1. Primary Sort: `ORDER BY district ASC`

* The database first sorts **all rows** based on the `district` column in **ascending** order (A-Z).
* The entire row (including the `address`, `district`, and other hidden columns) moves together to its correct position based on the `district` value.

### 2. Secondary Sort: `address DESC`

* The secondary sort only comes into play for rows that have **identical values** in the primary column (`district`).
* Within a single group of rows that share the same `district` name (e.g., all rows where `district` is 'Alberta'), those rows are then sorted by the `address` column in **descending** order (Z-A).

### 📝 Example Walkthrough

Let's imagine you have the following unsorted data:

| address | district |
| :---: | :---: |
| 45 Oak St | **B**rooklyn |
| 10 Pine Ln | **A**tlanta |
| 20 Main St | **B**rooklyn |
| 30 Birch Ave | **A**tlanta |

**Step A: Apply `district ASC`**

| address | district |
| :---: | :---: |
| 10 Pine Ln | **A**tlanta |
| 30 Birch Ave | **A**tlanta |
| 45 Oak St | **B**rooklyn |
| 20 Main St | **B**rooklyn |
*(The 'Atlanta' rows come before the 'Brooklyn' rows)*

**Step B: Apply `address DESC` within each district group**

* **For 'Atlanta':** The two rows are sorted by `address` in descending (Z-A) order.
* **For 'Brooklyn':** The two rows are sorted by `address` in descending (Z-A) order.

| address | district |
| :---: | :---: |
| **30 Birch Ave** | **A**tlanta | $\leftarrow$ '30 Birch' comes after '10 Pine' alphabetically
| **10 Pine Ln** | **A**tlanta |
| **45 Oak St** | **B**rooklyn | $\leftarrow$ '45 Oak' comes after '20 Main' alphabetically
| **20 Main St** | **B**rooklyn |

The resulting data set is completely stable and sorted based on your precise instructions!
