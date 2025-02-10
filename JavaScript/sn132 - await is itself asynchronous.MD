The author states in one point that "It is critical to understand right away that the `await` keyword does not cause your program to block and literally do nothing until the specified Promise settles. The code remains asynchronous, and the `await` simply disguises this fact. This means that any code that uses await is itself asynchronous."

And in another point:

```
let value1 = await getJSON(url1);

let value2 = await getJSON(url2);
```

The problem with this code is that it is unnecessarily sequential. the fetch of the second URL will not begin until the first fetch is complete."

For me that 2 statements contradict each other, one states "do no cause your program to block" and the other states "the second function will not begin until the first fetch is complete". Can you explain it to me?

---

[G] The author states in one point that "It is critical to understand right away that the `await` keyword does not cause your program to block and literally do nothing until the specified Promise settles. The code remains asynchronous, and the `await` simply disguises this fact. This means that any code that uses await is itself asynchronous."



And in another point:

```

let value1 = await getJSON(url1);

let value2 = await getJSON(url2);

```



The problem with this code is that it is unnecessarily sequential. the fetch of the second URL will not begin until the first fetch is complete."



For me that 2 statement contradict each other, one states "do no cause your program to block" and the other states "the second function will not begin until the first fetch is complete". Can you explain it to me?
