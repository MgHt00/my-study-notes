# Comparison Operators
- Less than (<)
- Greater than (>)
- Less than or equal (<=)
- Greater than or equal (>=)

ဒီ operator တွေအတွက် operand တွေက any type ဖြစ်လို့ ရပေမယ့် ၊ comparison တွေကိုတော့ number နဲ့ string တွေပေါ်မှာပဲ လုပ်ပါတယ်။ ဆိုတော့ကား .... ထုံးစံအတိုင်း number နဲ့ string မဟုတ်တဲ့ operand တွေကို convert လုပ်ရမပေ့ါ .... [^1]

### Comparison and conversion
- Operand ၂ ခုထဲက ၁ ခုက object ဖြစ်နေရင် primitive value ဖြစ်အောင် convert လုပ်ပါမယ်။ အကယ်လို့ valueof() method က primitive value တစ်ခု return လုပ်ရင် အဲ့ဒီ value ကို သုံးမယ်။ အဲလို့မှမဟုတ်ရင် toString() method ရဲ့ return value ကို သုံးမယ်။
- object-to-primitive conversion ပြီးသွားလို့ operand ၂ ခုလုံးက string ဖြစ်နေရင် string ၂ ခုကို compare လုပ်ပါမယ်။
- အကယ်လို့ object-to-primitive conversion ပြီးသွားလို့ operand ၁ ခုက string မဟုတ်ဘူးဆိုရင် ၊ operand ၂ ခုလုံးကို number ဖြစ်အောင်ပြောင်းပြီး compare လုပ်ပါမယ် (0 နဲ့ -0 က considered equal ၊ အကယ်လို့ operand တစ်ခုခုကို convert လုပ်လို့ NaN ထွက်ရင် comparison operator က always return false)။

### Favor and behavior
`+` operator က string ကို favor လုပ်ပြီး (operand ၁ ခုခုက string ဖြစ်နေနတာနဲ့ concatenation လုပ်ပါတယ်) comparison operator က number ကို favor လုပ်ပါတယ် (operand ၂ ခုလုံးက string ဖြစ်နေမှသာ string comparison လုပ်ပါတယ်)။

### Examples
`11 < 3` // => 3  
Numeric comparison လုပ်ပြီး false ထွက်ပါတယ်။

`"11" < "3"` // => true  
String comparison လုပ်ပြီး true ထွက်ပါတယ်။

`"11" < 3` // => false  
String 11 ကို number convert လုပ်ပြီး numeric convert လုပ်ပြီး compare လုပ်လို့ false ထွက်ပါတယ်။

`"one" < 3` //=> false  
one ကို convert လုပ်တော့ NaN ထွက်တာကြောင့် comparison က false ထွက်ပါတယ်။

[^1]: ဒီ post က ကျွန်တော်ပြန်ဖတ်ဖို့ ကျွန်တော့ရဲ့ ကိုယ်ပိုင် note တစ်ခုသာဖြစ်ပြီး [JavaScript: The Definitive Guide, 7th Edition by David Flanagan](https://www.oreilly.com/library/view/javascript-the-definitive/9781491952016/) စာအုပ်ကို refer လုပ်ထားပါတယ်ဗျာ။ 