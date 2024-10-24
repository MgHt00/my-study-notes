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
```javascript
