# The Conditional Operator (?:)[^1]
```javascript
first-operand ? second-operand : third-operand
```
first operand ကို evalute and interpret လုပ်ပြီး boolean ထုတ် ၊ truthy ဆိုရင် second operand ကို evaluate လုပ်ပြီး return ။ first operand က falsy ဆိုရင် third operand ကို evaluate လုပ်ပြီး value ကို return

#### Usage
```javascript
x > 0 ? x : -x
```

# First-Defined (??) [^2]
```javascript
(if left operand if not null and not undefined, return this) ?? (otherwise, return this)
```
`??` က first operand က nullish (null or undefined) ဖြစ်မဖြစ် စစ်ပါတယ်။ အဓိက point က nullish ပါ။

#### Usage
```javascript
a ?? b // equals to (a !== null && a!== undefined) ? a : b
```

# Logical AND (&&)[^3]
```javascript
falsy-value && truthy-value 
// If the value on the left is falsy, it returns the value on the left. 
// Value of the entire expression must be falsy.

truthy-value && falsy-value 
// If the value on the left is truthy, it evaluates and returns the value on the right.
```

#### Usage
```javascript
let o = {x: 1};
let p = null;
o && o.x; // => 1
p && p.x // => null

//short circuiting
(a === b) && stop(); // same as if (a === b) stop();
```

# Logical OR (||)[^4]
```javascript
truthy-value || some-value; 
// if the first operand is truthy, it short-circuits and returns that truthy value

falsy-value || some-value; 
// if the first operand is falsy, || evaluates its second operand and 
// returns the value of that expression.
```

`||` နဲ့ `??` ကွာတဲ့ main point က `||` က truthy/falsy ဖြစ် ၊ မဖြစ် ကို စစ်ပြီး `??` က nullish ဖြစ် ၊ မဖြစ် စစ်ပါတယ်။

### Usage
```javascript
let max = maxWidth || preferences.maxWidth || 500;
```

# Delete Operator[^5]
```javascript
let o = {x: 1, y: 2};
delete o.x;
```
`delete` က သူနဲ့တွဲဖို့ lvalue operand လိုပါတယ်။  lvalue မဟုတ်ရင် ဘာ action မှ မလုပ်သော်ငြား `true` ကို return ပြန်ပါတယ်။ 

Object property/ array element ကို delete operator သုံးပြီး delete လုပ်တဲ့အခါ `undefined` သတ်မှတ်ရုံသတ်မှတ်တာ မဟုတ်ပဲ ၊ လုံးလုံးဖျက်ပစ်လိုက်တာပါ။  ဘာမှ မရှိတဲ့ nonexisted property ကို access သွားလုပ်လို့ အဖြေက `undefined` ဖြစ်နေတာပါ။ 

Array element ကို ဖျက်လိုက်ရင် sparse array အဖြစ်ကျန်ခဲ့ပါတယ်။ 

မရှိတဲ့ property / array element ကိုဖျက်ရင် `true` ပဲ return ပြန်ပါတယ်။

# Logical Not (!)[^6]
သူ့ရဲ့ operand ကို boolean value ဖြစ်အောင် အရင်ပြောင်းပြီးမှ invert လုပ်ပါတယ်။  

any value `x` ကို သူ့ရဲ့ equivalent boolean value ဖြစ်အောင် ဒီလို ပြောင်းလို့ရပါတယ်။
```javascript
!!x
```

[^1]: JavaScript The Definitive Guide by David Flanagan - 4.13.1 (p. 91)
[^2]: 4.13.2 (p. 92)
[^3]: 4.10.1 (p. 84)
[^4]: 4.10.2 (p. 85)
[^5]: 4.13.4 (p. 94)
[^6]: 4.10.3 (p. 86)
