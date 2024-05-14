# Operator Side Effects

ကျွန်တော်ဖတ်နေတဲ့ စာအုပ်မှာ[^1] side effect ဆိုတာ မကြာခဏပါတယ်။ တွေ့တိုင်းလဲ ပြန်ပြန်ဖတ်နေရလို့ note အနေနဲ့ ရေးမှတ်ထားလိုက်ပါတယ်။ [^2]

ဥပမာ `2 * 3` ဆိုတဲ့ expression ကို evaluate လုပ်လို့ လက်ရှိ state သာမက program မှာ အနာဂတ် evalute လုပ်မယ့် expression မှာလဲ ဘာမှ အပြောင်းအလဲ ရှိလာမှာမဟုတ်ပါဘူး။ `2 * 3` result က အမြဲ 6 ထွက်နေမှာပါ။ 

ဒါပေမယ့် တချို့ expression တွေကျတော့ သူတို့ကို evaluation လုပ်လိုက်ခြင်းအားဖြင့် program မှာ အနာဂတ်ရှိလာမယ့် expression တွေရဲ့ result တွေပြောင်းလဲ သွားနိုင်ပါတယ်။ 

### Assignment Operators

အကယ်လို့ variable ဒါမှမဟုတ် property ထဲကို value တစ်ခု assign လုပ်လိုက်ပြီဆိုရင် အဲ့ဒီ အနာဂတ်မှာ အဲ့ဒီ variable ဒါမှမဟုတ် property ကိုသုံးမယ့် expression တွေရဲ့ result တွေကလဲ ပြောင်းလဲသွားတော့မှာပါ။

### ++ နဲ့ --

Increment နဲ့ decrement operator တွေကလဲ တကယ်တော့ implicit assignment ပဲမို့လို့ သူဟာလဲ side effect ပါပဲ။  ဥပမာအားဖြင့် `counter++` ဆိုတာက `counter = counter + 1;` ပဲလေ

### `delete` Operator

Object တစ်ခုရဲ့ property ကို delete လုပ်လိုက်တာဟာ property ကို undefined **assign** လုပ်လိုက်တာပဲမို့သူဟာလဲ side effect ပါပဲ။  အမှန်တော့ `delete` ဟာ object ရဲ့ property ကို undefined အပေါ်ယံ assign လုပ်လိုက်တာမဟုတ်ပဲ property ကို ဖျက်လိုက်ပြီး ၊ မရှိတော့တဲ့ property ကို access လုပ်နေတာမို့လို့ undefined ကို return ပြန်တာပါ။ [^3]

    let o = {x: 1, y: 2};
    delete o.x;

ဒီ code ပြီးလို့ 

    o.x;

ခေါ်ကြည့်ရင် `undefined` ထွက်ပါတယ်။ ဒါပေမယ့် ဒါဟာ undefined assign လုပ်ရုံသက်သက်မဟုတ်ပါဘူး။ 

    "x" in o 

နဲ့ ပြန်ကြည့်ရင် `o` ထဲမှာ `x` မရှိတော့တဲ့အတွက် `false` ထွက်ပါတယ်။

---

Array မှာဆိုရင်လဲ 

    let a = [1,2,3];
    delete a[1];

ဒီ code ပြီးလို့ `a` လို့ Chrome ရဲ့ console မှာ run ကြည့်ရင် `(3) [1, empty, 3]` လို့ ထွက်ပါတယ်။ `delete` operator က array မှာ hole တစ်ခုဖြစ်ကျန်အောင်လုပ်လိုက်ပေမယ့် array ရဲ့ length က မပြောင်းသွားပါဘူး။

    a.length;

ဆိုရင် `3` ပဲထွက်ပါတယ်။ 

### Function Invocation
    
Function invocation နဲ့ object creation expression တွေကလဲ သူတို့ရဲ့ function သို့မဟုတ် constructor body မှာပါတဲ့ operator တွေမှာ side effect တွေပါလာရင် သူတို့ဟာလဲ side effect ဖြစ်ပါတယ် (အကယ်လို့ function ဖြစ်လျက်နဲ့ side effect တစ်ခုမှ မပါဘူးဆိုရင်လဲ ဘာလုပ်ဖို့ function ကို call နေအုံးမှာလဲလေ)[^4]။ 


[^1]: ဒီ note က ကျွန်တော်ပြန်ဖတ်ဖို့ ကျွန်တော့ရဲ့ ကိုယ်ပိုင် note တစ်ခုသာဖြစ်ပြီး [JavaScript: The Definitive Guide, 7th Edition by David Flanagan](https://www.oreilly.com/library/view/javascript-the-definitive/9781491952016/) စာအုပ်ကို refer လုပ်ထားပါတယ်ဗျာ။  
[^2]: JavaScript: The Definitive Guide, 7th Edition - page 71  
[^3]: JavaScript: The Definitive Guide, 7th Edition - page 94  
[^4]: JavaScript: The Definitive Guide, 7th Edition - page 98