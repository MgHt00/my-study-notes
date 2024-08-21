| Category      | Sub-category |
| ----------- | ----------- |
|[Pseudo-Class Selectors](#pseudo-class-selectors)|-|
|[Structural Pseudo-Classes](#pseudo-class-selectors)<br><br><br><br><br><br><br><br><br><br><br>| <ul><li>:root</li> <li>[:empty](#empty10)</li> <li>[:only-child](#only-child4)</li> <li>[:only-of-type](#only-of-type5)</li> <li>:first-child</li> <li>:last-child</li> <li>:first-of-type</li> <li>:last-of-type</li> <li>:nth-child</li> <li>:nth-last-child</li> <li>:nth-of-type</li></ul>|
|[Location Pseudo-Classes](#location-pseudo-classes)<br><br><br><br><br><br><br><br><br><br><br>|<strong>[Hyperlink-specific pseudo-classes](#hyperlink-specific-pseudo-classes) <br> <ul><li>:link</li> <li>:visited</li> <li>:any-link</li> <li>:local-link</li></ul> <br> <strong>[Nonhyperlink location pseudo-classes](#nonhyperlink-location-pseudo-classes2)</strong><ul><li>:target</li> <li>:target-within</li> <li>:scope</li></ul> |
|[User Action Pseudo-Classes](#user-action-pseudo-classes3)||

# Combining Pseudo-Classes
Pseudo-class တွေကို combine(chain) လုပ်လို့ ရပါတယ်။ 
        
        a:link:hover {}

Specify လုပ်ထားတဲ့ order က အရေးမကြီးပါဘူး။ 

# Pseudo-Class Selectors

Pseudo-class selector တွေက phantom (not real; illusory) class တွေပါ။[^1] အဓိကအချက်က pesudo-class တွေက သူတို့ attached လုပ်ထားတဲ့ element တွေကိုပဲ refer လုပ်ပြီး သူတို့ရဲ့ decendent element တွေကို refer လုပ်တာမဟုတ်ပါဘူး။ ဥပမာ - 

    p:first-child {...}

မှာ `first-child` ဖြစ်တဲ့ `p` ကို ရည်ညွှန်းတာဖြစ်ပြီး `p` ရဲ့ `first-child` ကို ရည်ညွှန်းတာ မဟုတ်ပါဘူး။ 

# Structural Pseudo-Classes

- `:root`
- [`:empty`](#empty10)
- [`:only-child`](#only-child4)
- [`:only-of-type`](#only-of-type5)
- `:first-child`[^14]
- `:last-child`[^15] 
- `:first-of-type`[^16]
- `:last-of-type`
- `:nth-child`
- `:nth-last-child`
- `:nth-of-type`

## :empty[^11]

No children ဖြစ်တဲ့ any kind of element ကို select လုပ်မှာပါ။ ဒီမှာ element က 
- no whitespace
- no visible content
- no decendant element ဖြစ်ရပါမယ်။ 

CMS တွေမှာ ဘာ actual content မှ မပါတဲ့ element တွေကို supress လုပ်ချင်တဲ့ အခါ `p:empty {display: none;}` နဲ့ supress လုပ်လို့ ရပါတယ်။  

ထူးခြားတာက `<!--comment-->` ကို content လို့ မသတ်မှတ်တဲ့အပြင် ၊ whitespace လို့ပါ မသတ်မှတ်လို့ `<p><!--a comment--></p>` ဆိုရင် `p:empth {....);` နဲ့ အကျုံးဝင်ပါတယ်။  ဒါပေမယ့် comment ရဲ့ဘယ်ညာ မှာ space ထည့်မိတာ ၊ new line ယူမိတာဆိုရင်တော့ အကျုံးမဝင်တော့ပါဘူး။  

## :only-child[^12]
Element တစ်ခုက ငုံထားပြီး ငုံထားတဲ့ထဲမှာ သူတစ်ယောက်တည်း ရှိနေရင် `only-child` နဲ့ select လုပ်လို့ ရတယ် (အိ.... ငုံထားတာ .. ရွံစရာ :P) 

သတိထားရမှာက only-child ဖြစ်တဲ့ element ကို select လုပ်နေတာ ဖြစ်ပြီး သူ့ရဲ့ parent ကို select လုပ်ဖို့ကြိုးစားနေတာ မဟုတ်ပါဘူး။ 

နောက်တစ်ချက်က only-child ဆိုတဲ့ နေရာမှာ parent-child relationship ဖြစ်မှ ရမယ်ဆိုတာမျိုး မဟုတ်ပဲ decendant ဖြစ်ရုံနဲ့ ရပါတယ်။  ဥပမာ - `<a>` က ငုံထားတဲ့ `img:only-child`ကို select လုပ်ချင်တယ်ဆိုရင် 

        a
        |- img လဲအလုပ်ဖြစ်တယ်။

        a
        |- span
           |- img လဲ select လုပ်ပါတယ်။  

အကယ်လို့ `a` ရဲ့ child ဖြစ်ကိုဖြစ်ရမယ်၊ တစ်ယောက်တည်းကလဲ​ မွေးထားရအုံးမယ် ဆိုတဲ့ စွတ်အတင်းအတွက် ဆိုရင် - 

        a > img:only-child

## only-of-type[^13]
`a` က ငုံထားမယ် ပတ်ဝန်းကျင်မှာ သူနဲ့တူတာ မရှိဘူး ဆိုတဲ့သူကို select လုပ်ချင်ရင် `only-of-type` ကို သုံးရမှာပါ။ 

`a` က ငုံထားပြီး တစ်ခုတည်းပါတဲ့ `img` ကို select လုပ်မယ်ဆိုပါစို့ - 

        a
        |- b
        |- em
        |- img

        a img:only-of-typ 

`only-of-type` က တခြားသူတွေပါနေသော်လည်း သူပုံစံ (type) နဲ့ သူသာ ရှိတယ်ဆိုရင် select လုပ်မှာပါ။  ဒါက `only-child` နဲ့ ကွာတဲ့အချက်ပါ။ 

Type selector ကို element selector လို့ပြောင်းခေါ်သလိုပါပဲ။  ဒီနေရာမှာ type နဲ့ သူတစ်ယာက်တည်းဆိုတဲ့ စာကားလုံးကို သတိထားရပါမယ်။ 

        p.unique:only-of-type {color: red};

ဒီ code မှာ only-of-type ဖြစ်တဲ့ p (type / element) ကို အဓိက ဦးတည်မှာ ဖြစ်ပြီး class ကို အဓိကထားပြီး only-of-type ဖြစ်လား စစ်မှာမဟုတ်ပါဘူး။ 

        <div>
                <p class="unique">...</p>
                <p>...</p>
        </div>

ဒီလိုဆိုရင် `p.unique:only-of-type` က ဘေးမှာ sibling `<p>` ရှိနေတဲ့အတွက် `only-of-type` က ဘယ် `<p>` ကိုမှ select လုပ်မှာမဟုတ်ပါဘူး။ 

`p.unique:only-of-type` က အဓိပ္ပါယ်က - 

- `<p>` element ၊ ပတ်ဝန်းကျင်ကြားမှာ တစ်ခုတည်းပါနေတဲ့ `<p>` ဖြစ်ပြီး class attribute မှာ unique ပါနေတဲ့ `<p>` ကို select လုပ်ပါ။
- <em>`class=unique` ပါတဲ့ တစ်ခုတည်းရှိတဲ့ `<p>` ကို select လုပ်ခိုင်းနေတာ မဟုတ်ပါဘူး </em>

## nth-child[^00]

        div
        |- p
        |- ul
        |- p

ဒီ structure မှာ `p:nth-child(2)` ဆိုရင် နောက်ဆုံးက `p` ကို select <em>မလုပ်</em> ပါဘူး။

မှတ်ထားရမှာက - 2nd child ဟာ `p` ဖြစ်နေရင်လို့ ပြောတာပါ။ ဒုတိယမြောက် `p` လို့ ပြောချင်တာ မဟုတ်ပါဘူး။


# Location Pseudo-Classes

### Hyperlink-specific pseudo-classes

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
- :not()[^7]
- :is() and :where()[^8]
- :has()


# Logical Pseudo-Classes
### The negation pseudo-class

- `:not()`[^7]

        .moreinfo:not(li) {...}

.moreinfo class ရှိပြီး li မဟုတ်တဲ့ element တွေအားလုံးကို select လုပ်ပါမယ်။

- `:is()` and `:where()`[^8]


## The :has() Pseudo-Class

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
[^12]: page 56
[^13]: page 57
[^14]: page 59
[^15]: page 60
[^16]: page 61
[^00]: page 62