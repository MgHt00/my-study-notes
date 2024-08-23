| Category      | Sub-category |
| ----------- | ----------- |
|[Pseudo-Class Selectors](#pseudo-class-selectors)|-|
|[Structural Pseudo-Classes](#pseudo-class-selectors)<br><br><br><br><br><br><br><br><br><br><br>| <ul><li>:root</li> <li>[:empty](#empty10)</li> <li>[:only-child](#only-child4)</li> <li>[:only-of-type](#only-of-type5)</li> <li>:first-child</li> <li>:last-child</li> <li>:first-of-type</li> <li>:last-of-type</li> <li>:nth-child</li> <li>:nth-last-child</li> <li>:nth-of-type</li></ul>|
|[Location Pseudo-Classes](#location-pseudo-classes)<br><br><br><br><br><br><br><br><br><br><br>|<strong>[Hyperlink-specific pseudo-classes](#hyperlink-specific-pseudo-classes) <br> <ul><li>:link</li> <li>:visited</li> <li>:any-link</li> <li>:local-link</li></ul> <br> <strong>[Nonhyperlink location pseudo-classes](#nonhyperlink-location-pseudo-classes2)</strong><ul><li>:target</li> <li>:target-within</li> <li>:scope</li></ul> |
|[User Action Pseudo-Classes]()<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>|<ul><li> :enabled</li><li>:disabled</li><li>:checked</li><li>:indeterminate</li><li> :default</li><li>:autofill</li><li>:placeholder-shown</li><li>:valid</li><li>:invalid</li><li> :in-range</li><li>:out-of-range</li><li>:required</li><li>:optional</li><li> :read-write</li><li>:read-only</li></ul>|

# Combining Pseudo-Classes
Pseudo-class တွေကို combine(chain) လုပ်လို့ ရပါတယ်။ 
        
        a:link:hover {}

Specify လုပ်ထားတဲ့ order က အရေးမကြီးပါဘူး။ 

# 1. Pseudo-Class Selectors

Pseudo-class selector တွေက phantom (not real; illusory) class တွေပါ။[^1] အဓိကအချက်က pesudo-class တွေက သူတို့ attached လုပ်ထားတဲ့ element တွေကိုပဲ refer လုပ်ပြီး သူတို့ရဲ့ decendent element တွေကို refer လုပ်တာမဟုတ်ပါဘူး။ ဥပမာ - 

    p:first-child {...}

မှာ `first-child` ဖြစ်တဲ့ `p` ကို ရည်ညွှန်းတာဖြစ်ပြီး `p` ရဲ့ `first-child` ကို ရည်ညွှန်းတာ မဟုတ်ပါဘူး။ 

# Structural Pseudo-Classes

- `:root`
- [`:empty`](#empty10)
- [`:only-child`](#only-child4)
- [`:only-of-type`](#only-of-type5)
- `:first-child`[^2]
- `:last-child`[^3] 
- `:first-of-type`[^4]
- `:last-of-type`
- `:nth-child`
- `:nth-last-child`
- `:nth-of-type`[^5]

### :empty[^7]
---

No children ဖြစ်တဲ့ any kind of element ကို select လုပ်မှာပါ။ ဒီမှာ element က 
- no whitespace
- no visible content
- no decendant element ဖြစ်ရပါမယ်။ 

CMS တွေမှာ ဘာ actual content မှ မပါတဲ့ element တွေကို supress လုပ်ချင်တဲ့ အခါ `p:empty {display: none;}` နဲ့ supress လုပ်လို့ ရပါတယ်။  

ထူးခြားတာက `<!--comment-->` ကို content လို့ မသတ်မှတ်တဲ့အပြင် ၊ whitespace လို့ပါ မသတ်မှတ်လို့ `<p><!--a comment--></p>` ဆိုရင် `p:empth {....);` နဲ့ အကျုံးဝင်ပါတယ်။  ဒါပေမယ့် comment ရဲ့ဘယ်ညာ မှာ space ထည့်မိတာ ၊ new line ယူမိတာဆိုရင်တော့ အကျုံးမဝင်တော့ပါဘူး။  

### :only-child[^8]
---
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

### only-of-type[^9]
---
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

### nth-child[^10]
---

        div
        |- p
        |- ul
        |- p

ဒီ structure မှာ `p:nth-child(2)` ဆိုရင် နောက်ဆုံးက `p` ကို select <em>မလုပ်</em> ပါဘူး။

မှတ်ထားရမှာက - 2nd child ဟာ `p` ဖြစ်နေရင်လို့ ပြောတာပါ။ ဒုတိယမြောက် `p` လို့ ပြောချင်တာ မဟုတ်ပါဘူး။

`nth-child` မှာ နံပါတ်ထည့်လို့ရသလို `even`, `odd` နဲ့ အတူ algebraic expression ထည့်လို့ရပါတယ်။  Formula က 

        an + b
----
        an - b 

ဒီနေရမှာ formula က တစ်ဆက်တည်း မဟုတ်ပဲ `an` ကိုသပ်သပ် `+b`, `-b` ကို သပ်သပ် ခွဲမှတ်ထားတာ ပိုရှင်းပါတယ်။ `<li>` ကို ဥပမာ ယူမယ်ဆိုပါစို့ 

        +b => နေရာက စမယ် 
        -b => နေရာက စမယ်

        an => ရှေ့ဆက်တိုးသွားပြီး a အကြိမ်မြောက်တိုင်း ပြန်လုပ်မယ်
        -an => နောက်ဆုတ်သွားပြီး a အကြိမ်မြောက်တိုင်း ပြန်လုပ်မယ်

`li:nth-child(2n + 1);` ဆိုရင် ပထမဆုံး `li` ကနေစမယ် ၊ ၂ ခုမြောက်တိုင်း ပြန်လုပ်မယ်။ ဒါဆိုရင် 1, 3, 5 စသဖြင့် select လုပ်သွားမှာပါ။ 

`li:nth-child(4n - 2)` ဆိုရင် တကယ်မရှိသော်လည်း စိတ်ကူးထဲက -2 ခုမြောက် `li` က စမယ် ၊ ၄ ခုမြောက်တိုင်း select လုပ်မယ်။ ဆိုတော့ကား -2, 2, 6 စသဖြင့် select လုပ်ပေမယ့် ၊ -2 က စိတ်ကူးထဲက `li` ဖြစ်လို့ 2, 6 စသဖြင့် select လုပ်သွားမှာပါ။ 

`li:nth-child(-n + 5)` ဆိုရင် ၅ခုမြောက် `li` ကစမယ် တစ်ခုချင်းစီ နောက်ပြန်ဆုတ်သွားမယ်။ 

# 2. Location Pseudo-Classes
HTML ရဲ့ markup structure တစ်ခုတည်းကို ကြည့်ရုံနဲ့ ကြိုတင်ခန့်မှန်းလို့ မရတဲ့ အခြေအနတွေမှာ location pseudo-class တွေကို သုံးပါတယ်။ 

## 2.1.  Hyperlink-specific pseudo-classes[^11]

- `:link`
- `:visited`
- `:any-link`
- `:local-link`

## 2.2.  Nonhyperlink location pseudo-classes[^12]

- `:target`
- `:target-within`
- `:scope`

<em>Fragment identifier</em> ဆိုတဲ့ term နဲ့ အရင်ရင်းနီးဖို့ လိုပါတယ်။  ဥပမာ - www.mmls.biz/#new-arrival ဆိုတဲ့ link မှာ `#new-arrival` က fragment identifier ပါ။  

### :target
---
        *:target {...}

ဒီ style ထည့်ရေးထားမယ်ဆိုရင် ကိုယ့် page ကို visit လုပ်လာတဲ့ URL မှာ fragment identifier ပါလာတာနဲ့ HTML မှာရှိတဲ့ အဲ့ဒီ trageted element ကို select လုပ်မှာပါ။

`:target` က ဒီ အခြေနေ ၃ ခုမှာ မလုပ်မလုပ်ပါဘူး
- access လုပ်လာတဲ့ URL မှာ fragment identifier မပါတဲ့အခါ
- ပါတဲ့ fragment identifier က HTML ထဲမှာ ရှိတဲ့ ဘယ် element ရဲ့မှ မတူတဲ့အခါ
- scroll state ကို create မလုပ်ထားတဲ့ အခြေအနေနဲ့ page URL ကို update လုပ်လာတဲ့အခါ [^13]

### :target-within
---
`target` နဲ့ `target-within` ကွာတာက `target-within` က ကိုယ်တိုင် target ဖြစ်နေရင်ရော target မဟုတ်သော်ငြား target ရဲ့ parent ဖြစ်နေရင်ရော select လုပ်ပါတယ်။ [^14]

        p:target-within {..}

`p` ကိုယ်တိုင်က `#` ပါပြီး target ဖြစ်နရင် ဖြစ်ဖြစ် ၊ `p` ရဲ့ child element တစ်ခုခုက target ဖြစ်နေနရင် ဖြစ်ဖြစ် ဒီ style က အလုပ်လုပ်ပါတယ်။ [^15]

### :scope
---
`scope` က JS နဲ့ တွဲပြီး အလုပ်လုပ်ပါတယ်။

        let output = document.querySelector("#output");
        let registers = document.querySelectorAll(":scope > div");

ဆိုရင် #output အောက်မှာရှိတဲ့ div တွေအားလုံး registers ထဲရောက်မှာပါ။ 

# 3. User Action Pseudo-Classes[^16]

|Name   |Description    |
|-----  |--------       |
|`:hover`   |mouse pointer တင်ထားတဲ့ any element  |
|`:active`   |user input ကြောင့် activated ဖြစ်နေတဲ့ any element   |
|`:focus`   |လက်ရှိမှာ input focus ရှိနေတဲ့ any element   |
|`:focus-visible`| အခြေနေတစ်ခုခုမှာ browswer(user agent) က visible focus style ပေးသင့်တယ်လို့ သတ်မှတ်ထားတဲ့ element  |
|`:focus-within`   | focus ရှိတဲ့ any element (သို့) focus ရှိနေတဲ့ decendant ကို ပိုင်ထားနေတဲ့ element   |

ဒီ element တွေကို `:active`, `:focus` သုံးလို့ ရပါတယ်။
- links
- buttons
- menu items 
- `tabindex` value ပါတဲ့ any element
- any interactive elements
- form controls
- edit လုပ်လို့ရတဲ့ content ပါတဲ့ any element

Link တွေကို pseudo-class တွေနဲ့ styling လုပ်တဲ့အခါ ဒီ order အတိုင်းလုပ်ဖို့ recommend လုပ်ထားပါတယ်။

        link, visited, focus, hover, and active

<strong>L</strong>o<strong>V</strong>e <strong>F</strong>ears <strong>HA</strong>te လို့ မှတ်ရင် ပိုလွယ်ပါတယ်။[^17]

### :focus-visible
---
`:focus` နဲ့ တူသလို ရှိပေမယ့် ကွဲပြားတဲ့အချက်က အခြေနေတစ်ခုခုမှာ browswer(user agent) က visible focus style ပေးသင့်တယ်လို့ သတ်မှတ်ထားတဲ့ element ကိုပဲ match လုပ်မှာပါ။ 

ဥပမာ button တစ်ခုကို mouse နဲ့ click လုပ်ရင် `focus` ပေးနိုင်သလို ၊ keyboard နဲ့ click ရင်လဲ `focus` ပေးနိုင်ပါတယ်။ သို့ပေမယ့် accessibility နဲ့ aesthetics ကို အရေးပေးပြီး button ကို keyboard သို့မဟုတ် အခြား assistive technology သုံးပြီး focus လုပ်လာတဲ့အခါမှ `focus` ပေးချင်ပြီး mouse နဲ့ click / tap လုပ်လာတဲ့အခါ focus မပေးချင်ရင် `focus-visible` ကို သုံးရပါမယ်။

        button:focus-visible {outline: 5px solid maroon};
        
        /* 
        button ကို keyboard နဲ့ tab လုပ်လာတဲ့အခါ outline အကြီးကြီးပြပေးပြီး 
        mouse နဲ့ click လုပ်တဲ့အခါမှ ပြပေးမှာ မဟုတ်ပါဘူး။
        */

### :focus-within
---
Focus ရှိတဲ့ any element (သို့) focus ရှိနေတဲ့ decendant ကို ပိုင်ထားနေတဲ့ element ကို select လုပ်ပါတယ်။  ဥပမာ 

        nav (:focus-within ပေးထားမယ်)
        |- a (:focus ပေးထားမယ်)
        |- a (:focus ပေးထားမယ်)
        |- a (:focus ပေးထားမယ်)

ဒီလိုဆိုရင် `a` က focus ရတာနဲ့ `nav` ရဲ့ `focus-within` က အလုပ်လုပ်မှာပါ။ 

# 4. UI-State Pseudo-Classes[^18]
### 4.1 Enabled and disabled UI elements
|Name   | Description   |
|----   |---   |
|`:enabled`   |input လုပ်လို့ရတဲ့ / enable ဖြစ်နေတဲ့ UI element (form element လိုမျိုး) တွေ  |
|`:disabled`|input လုပ်လို့မရတဲ့ / disable ဖြစ်နေတဲ့ UI element (form element လိုမျိုး) တွေ|
----

### 4.2 Check states
|Name   | Description   |
|----   |---   |
|`:checked`|user ကြောင့် / default ကြောင့် select လုပ်ခံထားရတဲံ radio button (သို့) checkbox|
|`:indeterminate`|check မယ်ဆိုရပေမယ့် check လဲမဟုတ် uncheck လဲမဖြစ်တဲ့ radio button (သို့) checkbox (DOM scripting နဲ့ပဲ ဒီလို state ဖြစ်အောင် ဖန်တီးလို့ရပါတယ်။)[^19]|
---

### 4.3 Default-value pseudo-classes
|Name   | Description   |
|----   |---   |
|`:default`|selected by default ဖြစ်နေတဲ့ radio button, checkbox, or option | 
|`:autofill`|browser ကနေ autofill လုပ်ထားတဲ့ user input|
|`:placeholder-shown`|placeholder(not value) text ကြိုဖြည့်ထားတဲ့ user input |

#### Userful Codes
---
        input[type="checkbox"]:checked + label {
        ...
        }

---
        input:placeholder-shown {
                opacity: 0.75
        }

---
input:autofill {
                border: thick sold marooon;
        }
Browser က သတ်မှတ်ထားတဲ့ built-in autofill style တွေကို override လုပ်ရတာ ခက်ပါတယ်။ ဥပမာ browser သတ်မှတ်ထားတဲ့ autofill ရဲ့ background ကို override လုပ််လို့ မရပါဘူး။[^20]

### 4.4 Optionality pseudo-classes
|Name   | Description   |
|----   |---   |
|`:required`|value တစ်ခုခု set လုပ်ကိုလုပ်ထားရမယ့် user input|
|`:optional`|value တစ်ခုခု set လုပ်ထားစရာ မလိုတဲ့ user input|
---

### 4.5 Validity pseudo-classes
|Name   | Description   |
|----   |---   |
|`:valid`|သူ့ရဲ့ data validity requirement တွေအားလုံးနဲ့ ကိုက်ညီတဲ့ user input|
|`:invalid`|သူ့ရဲ့ data validity requirement တွေအားလုံးနဲ့ မကိုက်ညီတဲ့ user input|
** `:valid` နဲ့ `invalid` တွေကို data validity requirement capacity ရှိတဲ့ `<input>` လို element တွေမှာပဲ သုံးလို့ရပြီး `<div>` လို element တွေကို ဒီ pseudo-class နဲ့ select လုပ်လို့ ရမှာ မဟုတ်ပါဘူး။ [^21]

#### Userful Codes
---
        input[type="email"]:focus {
                background-positon: 100% 50%;
                background-repeat: no-repat;
        }

        input[type="email"]:focus:invalid {
                background-image: url(warning.jpg);
        }

        input[type="email"]:focus:valid {
                background-image: url(checkmark.jpg);
        }

---

### 4.6 Range pseudo-classes
|Name   | Description   |
|----   |---   |
|`:in-range`|သူ့ရဲ့ value က minimum နဲ့ maximum value ကြားထဲမှာ ရှိနေတဲ့ user input|
|`:out-of-range`|သူ့ရဲ့ value က control က ခွင့်ပြုထားတဲ့ minimum value ထက်နည်း (သို့) maximum ထက်များနေတဲ့ user input|

|`:read-write`|user က edit လုပ်ခွင့်ရှိတဲ့ user input|
|`:read-only`|user က edit လုပ်ခွင့် မရှိတဲ့ user input|

#### Userful Codes
---
        


### The :lang() and dir() Pseudo-Classes

- `:lang()` for example `*:lang(fr) {...}`[^00]
- `:dir()`  for example `*:dir(rtl) {...}`

### Logical Pseudo-Classes
- :not()[^00]
- :is() and :where()[^00]
- :has()


# Logical Pseudo-Classes
### The negation pseudo-class

- `:not()`[^00-]

        .moreinfo:not(li) {...}

.moreinfo class ရှိပြီး li မဟုတ်တဲ့ element တွေအားလုံးကို select လုပ်ပါမယ်။

- `:is()` and `:where()`[^00-]


## The :has() Pseudo-Class

- `:has()`

        div:has(img) {...}

`img` ပါတဲ့ div တွေအားလုံးကို select လုပ်ပါမယ်။ 

`:has()` ကို mythical "parent selector" လို့ ခေါ်နိုင်ပါတယ်။[^00]  

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

        :is(h1, h2, h3, h4, h5, h6):not(:has(img))[^00]

h1 ပဲဖြစ်ဖြစ် h3 ပဲဖြစ်ဖြစ် ၊ h ၆မျိုးလုံးအောက်မှာ `img` မပါတဲ့ heading တွေကို select လုပ်မှာပါ။

[^1]: ဒီ note က [CSS: The Definitive Guide, 5th Edition by Eric Meyer, Estelle Weyl](https://www.oreilly.com/library/view/css-the-definitive/9781098117603/) စာအုပ်ကို refer လုပ်ထားတာဖြစ်ပြီး ၊ ကျွန်တော်ပြန်ဖတ်ဖို့ ကျွန်တော့ရဲ့ ကိုယ်ပိုင် study note တစ်ခုသာဖြစ်လို့ အမှားပါကောင်းပါနိုင်ပါတယ်။  
[^2]: page 58
[^3]: page 60
[^4]: page 61
[^5]: page 66
[^7]: page 55
[^8]: page 56
[^9]: page 57
[^10]: page 62
[^11]: page 69
[^12]: page 71
[^13]: ကိုယ်တိုင် သိပ်နားမလည်ပါဘူး ၊ စာအုပ်ထဲပါတဲအတိုင်း မှတ်ထားတာပါ။ 
[^14]: page 72
[^15]: ၂၀၂၃ နှစ်စပိုင်းထိ `target-within` ကို browser တွေ support မလုပ်သေးဘူးလို့ သိရပါတယ်။ page 72
[^16]: page 74
[^17]: ([MDN web docs - Styling some links
](https://developer.mozilla.org/en-US/docs/Learn/CSS/Styling_text/Styling_links#styling_some_links))
[^18]: page 77
[^19]: page 78
[^20]: page 80
[^21]: page 81