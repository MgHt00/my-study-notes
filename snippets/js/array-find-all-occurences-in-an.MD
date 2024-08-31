# Finding all Occurences[^1]
### Find all occurrences of a value `x` in an array `a` and return an array of matching indexes

    function findall(a, x) {
      let results = [],
          len = a.length,
          pos = 0;

      while(pos < len) {
        pos = a.indexOf(x, pos);
        if (pos === -1) break;
        results.push(pos);
        pos = pos + 1;
      }
      return results;
    }

ပုံမှန်အားဖြင့် `indexOf()` ဒါမှမဟုတ် `lastIndexOf()` ကိုသုံးပြီးရှာရင် `x` ကို တွေ့တာနဲ့ index ကို return ပြန်မှာဖြစ်ပြီး ၊ တွေ့သမျှ `x` တွေရဲ့ index တွေကို array တစ်ခုနဲ့ သိမ်းထားချင်ရင် ဒီ snippet က အသုံးဝင်ပါတယ်။

[^1]: [JavaScript: The Definitive Guide, 7th Edition by David Flanagan](https://www.oreilly.com/library/view/javascript-the-definitive/9781491952016/) - page 175 မှာတဲ့ code snippet ပါ။ 