# A Function That Copies a Specified Number of Elements from One Array into Another Array[^1]

```javascript
function arraycopy ({from, to=from, n=from.length, fromIndex=0, toIndex=0}) {
  let valuesToCopy = from.slice(fromIndex, fromIndex + n);
  to.splice(toIndex, 0, ...valuesToCopy);
  return to;
}

let a = [1,2,3,4,5], b = [9,8,7,6,5];
arraycopy({from: a, n: 3, to: b, toIndex: 4});
```

[^1]: [JavaScript: The Definitive Guide, 7th Edition by David Flanagan](https://www.oreilly.com/library/view/javascript-the-definitive/9781491952016/) - page 198 မှာတဲ့ code snippet ပါ။ 