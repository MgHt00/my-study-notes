# Copy Missing Object Properties [^1]

    // Like Object.assign() but doesn't override existing properties
    function merge(target, ...sources) {    // source object တစ်ခုမက pass လုပ်ခဲ့သည် ရှိသော်
      for(let source of sources) {          // object တစ်ခုချင်းစီကို loop မယ်
        for(let key of Object.key(source) { // property တစ်ခုချင်းစီ loop မယ်
          if (!(key in target)) {           // this is different than Object.assign()
            target[key] = source[key];
        }
      }
      return target;
    }

    merge({x: 1}, {x: 1, y: 2}, {y: 3, z: 4});  // => {x: 1, y: 2: z: 4}

[^1]: [JavaScript: The Definitive Guide, 7th Edition by David Flanagan](https://www.oreilly.com/library/view/javascript-the-definitive/9781491952016/) - page 143 မှာတဲ့ code snippet ပါ။ 
