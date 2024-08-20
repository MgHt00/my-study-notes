# Pseudo-Class Selectors

Pseudo-class selector တွေက phantom (not real; illusory) class တွေပါ။[^1] အဓိကအချက်က pesudo-class တွေက သူတို့ attached လုပ်ထားတဲ့ element တွေကိုပဲ refer လုပ်ပြီး သူတို့ရဲ့ decendent element တွေကို refer လုပ်တာမဟုတ်ပါဘူး။ ဥပမာ - 

    p:first-child {...}

မှာ `first-child` ဖြစ်တဲ့ `p` ကို ရည်ညွှန်းတာဖြစ်ပြီး `p` ရဲ့ `first-child` ကို ရည်ညွှန်းတာ မဟုတ်ပါဘူး။ 

### Structural Pseudo-Classes

- `:root`
- [`:empty`](#empty10)
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
- `:placeholder-shown`
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

ဥပမာ - 

        section:has(table) {...}

ဒါဆိုရင် table ပါတဲ့ section ကို select လုပ်ပါမယ်။ parent selection ပေ့ါ။

---

        section:has(+ h2 em)

ဒါဆိုရင် အတွင်းမှာ `em` ပါတဲ့ `h2` ကပ်လိုက်နေတဲ့ section ကို select လုပ်မယ်။ 

        <section>....<section>
        <h2>... <em>...</em></h2>

sibling ပေါ်မူတည်ပြီး select လုပ်တာပေ့ါ။

---

        section:has(ol ul ol ol) {...}

ဒါဆိုရင် ဟိုး...ဘိုးဘေးဘီဘင် `section` ကို select လုပ်မယ့် ancestry chain ပါ။ 

ရှုပ်ရှုပ်ထွေးထွေးလေးကို ရှင်းရှင်းလင်းလင်း select လုပ်ချင်ရင် ဒီလိုလဲ ရပါတယ်။ 

        :is(h1, h2, h3, h4, h5, h6):not(:has(img))[^10]

h1 ပဲဖြစ်ဖြစ် h3 ပဲဖြစ်ဖြစ် ၊ h ၆မျိုးလုံးအောက်မှာ `img` မပါတဲ့ heading တွေကို select လုပ်မှာပါ။

## :empty[^11]

No children ဖြစ်တဲ့ any kind of element ကို select လုပ်မှာပါ။ ဒီမှာ elemet က 
- no whitespace
- no visible content
- no decendant element ဖြစ်ရပါမယ်။ 

CMS တွေမှာ ဘာ actual content မှ မပါတဲ့ element တွေကို supress လုပ်ချင်တဲ့ အခါ `p:empty {display: none;}` နဲ့ supress လုပ်လို့ ရပါတယ်။  

ထူးခြားတာက `<!--comment-->` ကို content လို့ မသတ်မှတ်တဲ့အပြင် ၊ whitespace လို့ပါ မသတ်မှတ်လို့ `<p><!--a comment--></p>` ဆိုရင် `p:empth {....);` နဲ့ အကျုံးဝင်ပါတယ်။  ဒါပေမယ့် comment ရဲ့ဘယ်ညာ မှာ space ထည့်မိတာ ၊ new line ယူမိတာဆိုရင်တော့ အကျုံးမဝင်တော့ပါဘူး။  

[^1]: ဒီ note က [CSS: The Definitive Guide, 5th Edition by Eric Meyer, Estelle Weyl](https://www.oreilly.com/library/view/css-the-definitive/9781098117603/) စာအုပ်ကို refer လုပ်ထားတာဖြစ်ပြီး ၊ ကျွန်တော်ပြန်ဖတ်ဖို့ ကျွန်တော့ရဲ့ ကိုယ်ပိုင် study note တစ်ခုသာဖြစ်လို့ အမှားပါကောင်းပါနိုင်ပါတယ်။  
[^2]: page 71
[^3]: page 74
[^4]: page 75
[^5]: page 77
[^6]: page 83
[^7]: page 84
[^8]: page 85
[^9]: page 89
[^10]: page 93
[^11]: page 55