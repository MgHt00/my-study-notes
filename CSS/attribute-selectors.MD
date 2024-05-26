# Attribute Selectors[^1]
Attribute selector တွေက element တစ်ခုရဲ့ attribute နဲ့ attribute ရဲ့ value တွေကို base လုပ်ပြီး element ကို select လုပ်မှာပါ။ [^2]

## Simple Attribute Selectors
Attribute ရဲ့ value ကိုထည့်စဥ်းစားစရာမလိုပဲ certain attribute ပါရုံပဲဆိုရင် simple attribute selector ကိုသုံးပါတယ်။ 

`h1` မှာ `class` ပါရုံနဲ့ select လုပ်မယ်ဆိုရင် - 
    
    h1[class] {...}

`img` မှာ `alt` ပါတာနဲ့ ဆိုရင် - 

    img[alt] {
        outline: 3px solid forestgreen;
    } 

`a` မှာ `href` ရော `title` ပါတာရောဆိုရင် - [^3]

     a[href][title] {...} 

## Selection Based on Exact Attribute Value
Attribute မှာ certain value ပါတဲ့ element တွေကိုပဲ select လုပ်မှာပါ။

    a[href="https://www.mmls.biz"] {...}

`urgent` နဲ့ `warning` class ပါတဲ့ `<p class="urgent warning">` ကို select လုပ်မယ်ဆိုရင် - 

    p[class="urgent warning"]

ဒီမှ သတိထားရမှာက html မှာ ရေးထားတဲ့ class name အစဥ်လိုက်အတိုင်းကို attribute selector ထဲမှာရေးမှ တူတယ်ဆိုပြီး select လုပ်မှာပါ။  

## Selection Based on Partial Attribue Values [^4]
<table border=1>
<tr>
<td width="20%">[foo~="bar"]</td>
<td>foo ဆိုတဲ့ attribute မှာ bar ဆိုတဲ့ စာလုံးက <strong>space-separated list</strong> အနေနဲ့ ပါနေတဲ့ element ကို select လုပ်မှာပါ။ </td>
</tr>
<tr>
<td>[foo*="bar"]</td>
<td>foo ဆိုတဲ့ attribute မှာ bar ဆိုတဲ့ စာလုံးက <strong>substring</strong> အနေနဲ့ ပါနေတဲ့ element ကို select လုပ်မှာပါ။</td>
</tr>
<tr>
<td>[foo^="bar"]</td>
<td>bar နဲ့ <strong>စတဲ့</strong> foo attribue ပါတဲ့ element ကို select လုပ်မှာပါ။</td>
</tr>
<tr>
<td>[foo$="bar"]</td>
<td>bar နဲ့ <strong>ဆုံးတဲ့</strong> foo attribue ပါတဲ့ element ကို select လုပ်မှာပါ။</td>
</tr>
<tr>
<td>[foo|="bar"]</td>
<td>bar နဲ့ <strong>စပြီးတာနဲ့ hyphen ပါတဲ့</strong> ဒါမှမဟုတ် value က <strong>exactly equal to bar</strong> ဖြစ်တဲ့ foo attribue ပါတဲ့ element ကို select လုပ်မှာပါ။
</td>
</tr>
</table>

### `|=` Examples
ဥပမာ - lang attribute က <em>equal to en</em> ဒါမှမဟုတ် <em>en-</em> ဖြစ်တဲ့ element ကို select လုပ်မယ်ဆိုရင် ဒီ attribute selector က အသုံးတည့်ပါပြီ။ [^5] 

    <h1 lang="en">Hello!</h1>
    <p lang="en-us">Greetings!</p>

    *[lang|="en"] {...}

HTML document မှာ `figure-1.jpg` `figure-2.jpg` စတဲ့ `figure-` နဲ့စတဲ့ `img` တွေကို select လုပ်ချင်တယ်ဆိုရင်- 

    img[src|="figure"] {
        border: 1px solid gray;
    }

---

### `~=` Examples
Class attribute မှာ space-separated list of words အနေနဲ့ `warning` ပါတဲ့ element ကို select လုပ်မယ်ဆိုရင်

    <p class="urgent warning">....</p>

    p[class~="warning"] {...}

`title` attribute မှာ space-separated list of words အနေနဲ့ `Figure` စာလုံး ပါတဲ့ `img`တွေကို border ထည့်မယ်ဆိုရင် 

    img[title~="Figure"] {
        border: 1px solid gray;
    }

သတိထားရမှာက `Figure` ဖြစ်မှ select လုပ်မှာဖြစ်ပြီး `figure` ဆိုရင် မလုပ်ပါဘူး။  <strong>case sensitive</strong> ဖြစ်ပါတယ်။  

---

### `*=` Examples
Attribute value ရဲ့ portion တစ်စိတ်တစ်ပိုင်းပေါ်လိုက်ပြီး select လုပ်မယ်ဆိုရင် 

    <span class="cloudy barren">Venus</span>

    span[class*="cloud"] {...}

`img` ရဲ့ source မှာ space ပါတာတွေ select လုပ်မယ်ဆိုရင် 

    img[src*="space"] {...}

Class name မှာ btn hyphen နဲ့ စပြီး -arrow ပါတဲ့ element ကို select လုပ်မယ်ဆိုရင်[^6]

    <button class="btn-small-arrow-active">Click Me</button>

    *[class|="btn"][class*="-arrow"] {...} 

---

### `^=` Examples
`https` နဲ့စတဲ့ `a` element တွေကို select လုပ်မယ်ဆိုရင်

    a[href^="https:"] {...}

`img` ရဲ့ `alt` မှာ Figure နဲ့ စတာတွေကို select လုပ်မယ်ဆိုရင် 

    img[src^="Figure"] {...}

---

### `$=` Examples

`.gif` နဲ့ ဆုံးတဲ့ img တွေကို select လုပ်မယ်ဆိုရင် 

    img[src$=".gif"] {...}

`.pdf` နဲ့ ဆုံးတဲ့ link တွေအားလုံးကို select လုပ်မယ်ဆိုရင် 

    a[href$=".pdf"] {...}

## The Case-Insensitivity Identifier [^7]
`.pdf` နဲ့ ဆုံးတဲ့နေရာမှာ link က `.pdf` ဖြစ်မလား ၊ `.PDF` ဖြစ်မလား ကြိုမသိနိုင်ရင် 

    a[href$=".pdf" i] {...}

နောက်ဆုံးမှာ <strong>i</strong> လေးထည့်ပေးလိုက်ရင်ရပါပြီ။  ဒီမှာသတိထားရမှာပါ `i` ထည့်ပေးလိုက်ခြင်းအားဖြင့် attribute တွေရဲ့ value တွေပဲ case-<em>in</em>sensitve ဖြစ်သွားပြီး attribute name တွေကတော့ case-sensitive ဖြစ်မြဲပါ။

အပေါ်က example မှာ `i` ထည့်လိုက်ခြင်းအားဖြင့် `.pdf` သာ case-insensitive ဖြစ်သွားပြီး attribute ဖြစ်တဲ့ `href` ကတော့ case-sensitive ဖြစ်မြဲတိုင်းပါ။ 

[^1]: ဒီ note က [CSS: The Definitive Guide, 5th Edition by Eric Meyer, Estelle Weyl](https://www.oreilly.com/library/view/css-the-definitive/9781098117603/) စာအုပ်ကို refer လုပ်ထားတာဖြစ်ပြီး ၊ ကျွန်တော်ပြန်ဖတ်ဖို့ ကျွန်တော့ရဲ့ ကိုယ်ပိုင် study note တစ်ခုသာဖြစ်လို့ အမှားပါကောင်းပါနိုင်ပါတယ်။  
[^2]: page - 34
[^3]: page 35
[^4]: page 37
[^5]: page 37
[^6]: page 40
[^7]: page 42