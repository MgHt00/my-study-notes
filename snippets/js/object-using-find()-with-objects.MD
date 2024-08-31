# Using find() with Objects[^1]
### find() Method:
find() allows you to search for an element in an array based on a condition (predicate function) that you define.

You can write a custom function that checks the content of the objects, rather than relying on reference equality.

Example:

    let arr = [{ name: "Alice" }, { name: "Bob" }, { name: "Alice" }];

    let result = arr.find(obj => obj.name === "Alice");
    console.log(result); // { name: "Alice" } (returns the first matching object)

In this example, find() looks for an object where the name property is "Alice". It doesn't care about the reference, just the content.

[^1]: ChatGPT က ရထားတဲ့ code ပါ။ 