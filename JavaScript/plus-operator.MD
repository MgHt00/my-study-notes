# The `+` Operator
Binary operator တစ်ခုဖြစ်တဲ့ + operator ဟာ
- numeric operand တွေကို add လုပ်ပေးသလို
- string operand တွေကို concatenate လုပ်ပေးပါတယ်။ [^1]

`1+2` // => 3 

`"1" + "2"` // => '12'

`"hello" + " " + "Mg Htoo"` // => "hello Mg Htoo"

ဒါဆို နောက်ကွယ်မှာ ဘယ်လို အလုပ်လုပ်တာလဲ?

အကယ်လို့ operand တစ်ခုက string ဖြစ်နေမယ် ဒါမှမဟုတ် string ဖြစ်အောင်ပြောင်းလို့ ရတဲ့ object တစ်ခု ဖြစ်နေမယ်ဆိုရင် ၊ ကျန်တဲ့ operand ကို string ဖြစ်အောင် ပြောင်းပြီး + operator က concatenation ကို perform လုပ်ပါတယ်။

operand တွေက string-like မဟုတ်ဘူးဆိုရင်တော့ addition ကို perform လုပ်ပါတယ်။

### Technically
- အကယ်လို့ operand တစ်ခုက object ဆိုရင် object-to-primitive algorithm ကိုသုံးပြီး primitive တစ်ခုဖြစ်အောင် အရင်ဆုံး convert လုပ်ပါတယ်။
- object-to-primitive conversion ပြီးသွားတဲ့အခါ ၊ operand ၂ ခုထဲက ၁ ခုက string ဖြစ်နေမယ်ဆိုရင် ကျန်တဲ့တစ်ခုကို string ဖြစ်အောင် convert လုပ်ပြီး concatenation ကို perform လုပ်ပါတယ်။
- ဒီလိုမှ မဟုတ်ရင်တော့ operand ၂ ခုလုံးကို number တွေအဖြစ် (ဒါမှမဟုတ် NaN) အဖြစ် convert လုပ်ပြီး addition ကို perform လုပ်ပါတယ်။

### More Examples
`"1" + "2"` // => '12'  
တစ်ဖက် string ဖြစ်နေတာကြောင့် concatenation ကို perform လုပ်ပါတယ်။

---

`1 + {}` // => `1[object Object]`  
{ } ကို object-to-primitive နဲ့ convert လုပ်တော့ [object Object] ထွက်တာကြောင့် concatenation ကိုပဲ perform လုပ်ပါတယ်။

---

`true + true` // => 2  
true က boolean truthy value : 1 ဖြစ်တာကြောင့် 1 + 1 = 2 ၊ addition ကို perform လုပ်ပါတယ်။

---

`2 + null` // => 2  
ဒါက နည်းနည်းကြောင်ပါတယ်။ null က 0 အဖြစ် convert လုပ်တာကြောင့် 2 + 0 addition perform လုပ်ပြီး 2 ထွက်ပါတယ်။

---

`2 + undefined` // => NaN  
undefined ကို convert လုပ်တော့ NaN ထွက်တာကြောင့် 2 + NaN addition မှာ အဖြေက NaN ထွက်လာပါတယ်။

### Order of Operation  
`+` operator ကို string ၊ number တွေနဲ့ သုံးတဲ့အခါ operator associativity ထက် order of operation ကို ပိုပြီး depend လုပ်သွားမှာပါ။

`1 + 2 + "blind mice"` // => '3 blind mice'  
အပေါ်က example မှာ order of operation ကို ( ) parentheses နဲ့ explicitly ကြေငြာထားတာ မရှိတဲ့အတွက် left to right associativity နဲ့ perform လုပ်ပါတယ်။

`1 + (2 + " blind mice")` // => '12 blind mice'  
ဒီ example မှာတော့ ( ) parentheses ပါတဲ့ အတွက် number 2 ကို string နဲ့ အရင် concatenate လုပ်ပြီးတော့မှ 1 နဲ့ ထပ်ပြီး concatenate လုပ်ပါတယ်။

[^1]: ဒီ post က ကျွန်တော်ပြန်ဖတ်ဖို့ ကျွန်တော့ရဲ့ ကိုယ်ပိုင် note တစ်ခုသာဖြစ်ပြီး [JavaScript: The Definitive Guide, 7th Edition by David Flanagan](https://www.oreilly.com/library/view/javascript-the-definitive/9781491952016/) စာအုပ်ကို refer လုပ်ထားပါတယ်ဗျာ။ 
