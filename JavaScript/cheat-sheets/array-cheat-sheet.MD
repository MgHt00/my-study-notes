# Arrays
## 1. Creating Arrays[^1]
### 1.1 Array Literals
Square bracket ထဲမှာ comma-separated list 
```javascript
let empty = [];
let primes = [2, 3, 5, 7, 11];
```

### 1.2 The Spread Operator
Spread operator က array တစ်ခုကို (shallow) copy လုပ်ဖို့ သုံးလို့ကောင်းပါတယ်။
```javascript
let original = [1, 2, 3];
let copy = [...original];
```
String က iterable ဖြစ်တာကြောင့် spread operator သုံးပြီး single-character string လုပ်လို့ရပါတယ်။ 
```javascript
let digits = [..."0123456789ABCDEF"];
```

### 1.3 The Array() Constructor
- argument မပါပဲ call:
```javascript
let a = new Array();
```
- single numeric argument (which specifies a length) နဲ့ call
```javascript
let a = new Array(10); // value 10 ထည့်တာမဟုတ်ပဲ ၊ array ၁၀ ခန်း ဆောက်တာပါ
```

- two or more array element ဒါမှမဟုတ် single non-numeric element နဲ့ call
```javascript
let a = new Array(5, 4, 3, 2);
let b = new Array("c");
```

[^1]: JavaScript The Definitive Guide by David Flanagan - 7.1 (p. 156)
