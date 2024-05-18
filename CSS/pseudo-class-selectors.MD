# Pseudo-Class Selectors

Pseudo-class selector တွေက phantom (not real; illusory) class တွေပါ။[^1] အဓိကအချက်က pesudo-class တွေက သူတို့ attached လုပ်ထားတဲ့ element တွေကိုပဲ refer လုပ်ပြီး သူတို့ရဲ့ decendent element တွေကို refer လုပ်တာမဟုတ်ဘူးဆိုတာပါ။ ဥပမာ - 

    p:firt-child {...}

မှာ `first-child` ဖြစ်တဲ့ `p` ကို ရည်ညွှန်းတာဖြစ်ပြီး `p` ရဲ့ `first-child` ကို ရည်ညွှန်းတာ မဟုတ်ပါဘူး။ 

### Structural Pseudo-Classes

- `:root`
- `:empty`
- `:only-child`
- `:only-of-type`
- `:first-child`
- `:last-child`
- `:first-of-type`
- `:last-of-type`
- `:nth-child`
- `:nth-last-child`
- `:nth-of-type`

### Location Pseudo-Classes

#### Hyperlink-specific pseudo-classes

- `:link`
- `:visited`
- `:any-link`
- `:local-link`

#### Nonhyperlink location pseudo-classes[^2]

- `:target`
- `:target-within`
- `:scope`

### User Action Pseudo-Classes[^3]

- `:hover`
- `:active`
- `:focus`
- `:focus-within`
- `:focus-visible`[^4]

### UI-State Pseudo-Classes[^5]

- `:enabled`
- `:disabled`
- `:checked`
- `:indeterminate`
- `:default`
- `:autofill`
- `placeholder-shown`
- `:valid`
- `:invalid`
- `:in-range`
- `:out-of-range`
- `:required`
- `:optional`
- `:read-write`
- `:read-only`

### The :lang() and dir() Pseudo-Classes

- `:lang()` for example `*:lang(fr) {...}`[^6]
- `:dir()`  for example `*:dir(rtl) {...}`

### Logical Pseudo-Classes

#### The negation pseudo-class

- `:not()`[^7]

        .moreinfo:not(li) {...}

.moreinfo class ရှိပြီး li မဟုတ်တဲ့ element တွေအားလုံးကို select လုပ်ပါမယ်။

- `:is()` and `:where()`[^8]


### The :has() Pseudo-Class

- `:has()`

        div:has(img) {...}

`img` ပါတဲ့ div တွေအားလုံးကို select လုပ်ပါမယ်။ 

`:has()` ကို mythical "parent selector" လို့ ခေါ်နိုင်ပါတယ်။[^9]  

1. `:has()`ဟာ parent selection လုပ်နိုင်ရုံမက
2. sibiling တွေပေါ်မူတည်ပြီး select လုပ်လို့ရသလို
3. ancestry chain အဝေးကြီးထိလိုက်ပြီး select လုပ်လို့ရပါတယ်။ 



[^1]: ဒီ note က [CSS: The Definitive Guide, 5th Edition by Eric Meyer, Estelle Weyl](https://www.oreilly.com/library/view/css-the-definitive/9781098117603/) စာအုပ်ကို refer လုပ်ထားတာဖြစ်ပြီး ၊ ကျွန်တော်ပြန်ဖတ်ဖို့ ကျွန်တော့ရဲ့ ကိုယ်ပိုင် study note တစ်ခုသာဖြစ်လို့ အမှားပါကောင်းပါနိုင်ပါတယ်။  
[^2]: page 71
[^3]: page 74
[^4]: page 75
[^5]: page 77
[^6]: page 83
[^7]: page 84
[^8]: page 85
[^9]: page 89