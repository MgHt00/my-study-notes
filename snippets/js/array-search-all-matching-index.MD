The following funciton searches an array for a specified value and returns an array of all matching indexes.[^1]

    function findall(a, x) {
      let results = [],
          len = a.length,
          pos = 0;

          while(pos < len) {
            pos = a.index(x, pos);
            if (pos === -1) break;
            results.push(pos);
            pos = pos + 1;
          }
          return results;
    }

[^1]: ([CSS: The Definitive Guide, 5th Edition by Eric Meyer, Estelle Weyl](https://www.oreilly.com/library/view/css-the-definitive/9781098117603/)) page 174 မှာပါတဲ့ snippet ပါ။