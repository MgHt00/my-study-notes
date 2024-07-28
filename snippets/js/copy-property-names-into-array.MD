# To copy the names of all object properties into an array [^1]

    let o = {
      x: 1,
      y: 2,
      Z: 3,
    }

    let a = [], i = 0;

    for (a[i++] in o) /* empty */;

In this code, an empty space after for/in loop is essential, it will not work otherwise. 

[^1]: [JavaScript: The Definitive Guide, 7th Edition by David Flanagan](https://www.oreilly.com/library/view/javascript-the-definitive/9781491952016/) - page 112 မှာတဲ့ code snippet ပါ။ 
