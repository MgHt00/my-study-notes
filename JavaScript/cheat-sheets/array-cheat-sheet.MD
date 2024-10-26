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

### 1.4 Array.of()
Factory method ဖြစ်လို့ `new` နဲ့ call စရာမလိုပါဘူး။ ပေးထားတဲ့ argument ကိုသုံးပြီး new array ကို return ပါတယ်။  
```javascript
Array.of(); // => []
Array.of(10); // => [10] ဒီမှာ new Array(10) သုံးတာနဲ့ ကွာပါတယ်။
Array.of(1,2,3); // => [1,2,3]
```
### 1.5 Array.from()
Factory method ပါ။  array-like object ကို true-array ဖြစ်အောင် လုပ်ပေးနိုင်ပါတယ်။

## 2. Reading and Writing Array Elements[^2]
Array တွေက specialized kind of object တွေပါ။ 

JavaScript က array အတွက်ပေးလိုက်တဲ့ numeric index ကို string ဖြစ်အောင် convert လုပ်ပါတယ်။  ဒါကြောင့် index 1 က string "1" ဖြစ်သွားပြီး အဲဒီ string ကို property name အဖြစ်သုံးပါတယ်။

Array index တိုင်းက property name ဖြစ်ပေမယ့် 0 - 2<sup>32<sup>-2 (non-negative integer) ဖြစ်တဲ့ property name တွေပဲ array index ဖြစ်နိုင်ပါတယ်။


[^1]: JavaScript The Definitive Guide by David Flanagan - 7.1 (p. 156)
[^2]: 7.2 (p. 159)
