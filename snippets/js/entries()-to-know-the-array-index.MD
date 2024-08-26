# `entries()` method of the array

If you want to use a for/of loop for an array and need to know the index of each array element, use the `entries()` method of the array, along with destructruing assignment: [^1]

    let everyother = "";
    for(let [index, letter] of letters.entries()) {
      if (index % 2 === 0) everyother += letter; // letters at even index
    }
  
[^1]: ဒီ snippet က ([CSS: The Definitive Guide, 5th Edition by Eric Meyer, Estelle Weyl](https://www.oreilly.com/library/view/css-the-definitive/9781098117603/)) ရဲ့ page 163 မှာပါပါတယ်။ 