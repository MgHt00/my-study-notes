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

Array အတွက်ပေးလိုက်တဲ့ numeric index ကို JavaScript က string ဖြစ်အောင် convert လုပ်ပါတယ်။  ဒါကြောင့် index 1 က string "1" ဖြစ်သွားပြီး အဲဒီ string ကို property name အဖြစ်သုံးပါတယ်။

Array index တိုင်းက property name ဖြစ်နိုင်ပေမယ့် 0 နဲ့ 2<sup>32</sup> - 2 ကြား (non-negative integer) ဖြစ်တဲ့ property name တွေပဲ array index ဖြစ်နိုင်ပါတယ်။

Array တိုင်းက object ဖြစ်တာကြောင့် property with any name ကို array မှာ create လုပ်လို့ ရပါတယ်။  အကယ်လို့ array index တွေကို property name အဖြစ်သုံးရင်တော့ ၊ `length` property ကို update လုပ်နိုင်တဲ့ behavior တစ်ခု array မှာ ရှိပါတယ်။  

အကယ်လို့ non-negative integer တစ်ခုက string အဖြစ် (`" "`) နဲ့ object property လုပ်ပါလို့ သတ်မှတ်ပေးလိုက်ရင် ၊ string ဖြစ်သော်ငြားလဲ non-negative integer ဖြစ်တာကြောင့် array index တစ်ခု အနေနဲ့ behave လုပ်ပါတယ်။
```javascript
a["1000"] =  0; // This is the 1001st element of the array
a["1.000"] = 1; // Array index 1. Same as a [1] = 1;
```
Javascript array တွေမှာ "out of bounds" error မရှိပါဘူး။  ဒါကြောင့် nonexistent property ကို query လုပ်ရင် error ထွက်မှာမဟုတ်ပဲ `undefined` ပဲ ထွက်လာပါလိမ့်မယ်။ (Array တင်မဟုတ်ပဲ object မှာလဲ ဒီလိုပဲဖြစ်ပါတယ်။)

## 3. Sparse Array[^3]
`Array()` constructor သုံးပြီး ဒါမှမဟုတ် current array length ထက်ပိုကြီးတဲ့ array index သတ်မှတ်ပြီး sparse array တွေ ဖန်တီးနိုင်ပါတယ်။
```javascript
let a = new Array(5); // No element, but a.length is 5.
a = [];               // Create an array with no elements and length = 0.
a[1000] = 0;          // Assignment adds one element but sets length to 1001.
```
`delete` operator သုံးလိုက်ရင်လဲ sparse array ဖြစ်သွားပါတယ်။ 
```javascript
let b = [1,2,3];
delete b[1]; // => b = [1, , 3];
```
Array literal မှာ value ကို omit လုပ်ရင်လဲ sparse array ထွက်ပါတယ်။  
```javascript
let a1 = [,] // နောက်ဆုံး comma က tailing comma ပါ။ ဒါကြောင့် comma နောက်က element က sparse မဟုတ်ပဲ ...
             // ... length စစ်ရင် 1 ပဲ ထွက်ပါလိမ့်မယ်။   
```
Sparse array တွေနဲ့ အလုပ်လုပ်တဲ့အခါ code တွေက sparse array ကို `undefined` element တွေဖြည့်ထားတဲ့ nonsparse array တစ်ခုအနေနဲ့ပဲ treat လုပ်ပါလိမ့်မယ်။

[^1]: JavaScript The Definitive Guide by David Flanagan - 7.1 (p. 156)
[^2]: 7.2 (p. 159)
[^3]: 7.3 (p. 160)
