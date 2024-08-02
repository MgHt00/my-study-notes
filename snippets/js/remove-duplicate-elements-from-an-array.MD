# Remove Duplicate Elements From An Array[^1]

Set objects are iterable, so an easy way to remove duplicate elements from an array is to convert the array to a set and then immediately convert the set back to an array using the spread operator:

    let letters = [..."hello world"];
    console.log([...new Set(letters)]);
    

`(8) ['h', 'e', 'l', 'o', ' ', 'w', 'r', 'd']`

[^1]: [JavaScript: The Definitive Guide, 7th Edition by David Flanagan](https://www.oreilly.com/library/view/javascript-the-definitive/9781491952016/) - page 112 မှာတဲ့ code snippet ပါ။ 
