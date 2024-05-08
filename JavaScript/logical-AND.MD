# Logical AND `&&`

`&&` operator က level ၃ ခုနဲ့ အလုပ်လုပ်ပါတယ်။ [^1]

*** Simplest Level
Boolean operand တွေနဲ့ အလုပ်လုပ်တဲ့ simplest level ပါ။ First operand ရော second operand ပါ true ဖြစ်ရင် true return ပြန်ပါမယ်။ 

`x === 0 && y === 0`

Relational expresion တိုင်းဟာ true သို့မဟုတ် false အမြဲတမ်း evaluate လုပ်တာမို့ `&&` ကို relational expression နဲ့တွဲသုံးရင် true သို့မဟုတ် false ပဲ return ပြန်မှာပါ။

### Second Level
ဒါက truthy and flasy value တွေတွက်ပါ။  JavaScript မှာ boolean value ကို expect လုပ်တဲ့ ဘယ် expression, statement မဆို truthy / flasy value နဲ့ အလုပ်လုပ်တာကြောင့် `&&` ဟာ အမြဲတမ်း true / false ပဲ retrn လုပ်နေမှာမဟုတ်သလို true / flase မဟုတ်လို့ ဘာ problem မှလဲ ပေးမှာမဟုတ်ပါဘူး။

Second level မှာ operand ၂ ခုလုံးက truthy ဖြစ်နေရင် truthy တစ်ခုက falsy ဖြစ်နေရင် falsy return လုပ်မှာပါ။

### Final Level
ဒါဆိုရင် truthy မှာမှ ဘယ် truthy ကို return မှာလဲ flasy value တွေအများကြီးရှိတဲ့ထဲက ဘယ် falsy value ကို return လုပ်မှာလဲဆိုတဲ့ ကိစ္စက third level ပါ။  

ပထမ operand ကိုစပြီး evaluate လုပ်လို့ flasy ဆိုရင် entire expression က falsy ဖြစ်ပြီး `&&` က ကျန်တဲ့ operand ကို ဆက်မကြည့်ပါဘူး။ 

အကယ်လို့ value on the left က truthy ဖြစ်နေပြီဆိုရင် overall value of the expression က ကျန်တဲ့ operand ပေါ်မှာ မူတည်ပါတယ်။ **ဒါကြောင့် value on the left က truthy ဖြစ်နေပြီဆိုရင် `&&` operator က value on the right ကို evaluate လုပ်ပြီး value on the right ကိုပဲ return ပြန်ပါတယ်။** 


`let o = {x: 1};`  
`let p = null;`  
`o && o.x;` // => 1 ထွက်ပါတယ်။  ဘယ်ဖက် operand က truthy ဖြစ်နေလို့ ညာဖက်ကိုဆက်ကြည့်တော့ ရလာတဲ့ အဖြေက 1 မို့လို့ 1 ကို return ပြန်ပါတယ်။  
`p && p.x;`  // => null ပါ။  p ကို evaluate လုပ်တဲ့အခါ null ဖြစ်နေတာကြောင့် ညာဖက်ကို ဆက်မကြည့်တော့ပါဘူး။

နောက်ဆုံးလိုင်းက အကယ်လို့ p.x ကိုသာဆက်ပြီး evaluate လုပ်မယ်ဆိုရင် TypeError ထွက်မှာပါ။ 

ရှေ့ကမှန်မှ နောက်ကိုဆက်လုပ်မယ့် အစွမ်းကြောင့် `&&` ကိို short circuiting လို့လဲခေါ်ပါတယ်။ ဥပမာအားဖြင့် 

`if(a === b) stop();` ဒီလိုင်းအစား  
`(a === b) && stop();` ဒီလိုရေးလို့ရပါတယ်။  a === b က true ဖြစ်မှ stop() ကို ဆက်ပြီးအလုပ််လုပ်မှာပါ။ [^2]

မောင်ထူး

[^1]: ဒီ post က ကျွန်တော်ပြန်ဖတ်ဖို့ ကျွန်တော့ရဲ့ ကိုယ်ပိုင် note တစ်ခုသာဖြစ်ပြီး [JavaScript: The Definitive Guide, 7th Edition by David Flanagan](https://www.oreilly.com/library/view/javascript-the-definitive/9781491952016/) စာအုပ်ကို refer လုပ်ထားပါတယ်ဗျာ။ 

[^2]: ဒီ note က ကျွန်တော်တဲ့ study note သီးသန့်သာဖြစ်ပြီး အမှားပါနိုင်ပါတယ်။ အမှန်အမှား သံသယရှိရင် MDN site နဲ့ မူရင်းစာအုပ်ကို ကိုးကားစေချင်ပါတယ်။

