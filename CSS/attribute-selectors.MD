# Attribute Selectors
Attribute selector တွေက element တစ်ခုရဲ့ attribute နဲ့ attribute ရဲ့ value တွေကို base လုပ်ပြီး element ကို select လုပ်မှာပါ။ [^1]


[^1]: ဒီ note က [CSS: The Definitive Guide, 5th Edition by Eric Meyer, Estelle Weyl](https://www.oreilly.com/library/view/css-the-definitive/9781098117603/) စာအုပ်ကို refer လုပ်ထားတာဖြစ်ပြီး ၊ ကျွန်တော်ပြန်ဖတ်ဖို့ ကျွန်တော့ရဲ့ ကိုယ်ပိုင် study note တစ်ခုသာဖြစ်လို့ အမှားပါကောင်းပါနိုင်ပါတယ်။  pg - 34
[^2]: CSS: The Definitive Guide, 5th Edition -  page 87

## Simple Attribute Selectors
Attribute ရဲ့ value ကိုထည့်စဥ်းစားစရာမလိုပဲ certain attribute ပါရုံပဲဆိုရင် simple attribute selector ကိုသုံးပါတယ်။ 

`h1` မှာ `class` ပါရုံနဲ့ select လုပ်မယ်ဆိုရင် - 
    
    h1[class] {
        ...
    }

`img` မှာ `alt` ပါတာနဲ့ ဆိုရင် - 

    img[alt] {
        outline: 3px solid forestgreen;
    } [^2]

`a` မှာ `href` ရော `title` ပါတာရောဆိုရင် - 

     a[href][title] {
        ...
    }

## Selection Based on Exact Attribute Value
Attribute မှာ certain value ပါတဲ့ element တွေကိုပဲ select လုပ်မှာပါ။

    a[href="https://www.mmls.biz"] {
        ...
    }

`urgent` နဲ့ `warning` class ပါတဲ့ `<p class="urgent warning">` ကို select လုပ်မယ်ဆိုရင် - 

    p[class="urgent warning"]

ဒီမှ သတိထားရမှာက html မှာ ရေးထားတဲ့ class name အစဥ်လိုက်အတိုင်းကို attribute selector ထဲမှာရေးမှ တူတယ်ဆိုပြီး select လုပ်မှာပါ။  

## Selection Based on Partial Attribue Values [^3]
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

### `[foo|=bar]` Examples
ဥပမာ - lang attribute က <em>equal to en</em> ဒါမှမဟုတ် <em>en-</em> ဖြစ်တဲ့ element ကို select လုပ်မယ်ဆိုရင် ဒီ attribute selector က အသုံးတည့်ပါပြီ။  

    *[lang|="en"] {
        ...
    }

HTML document မှာ `figure-1.jpg` `figure-2.jpg` စတဲ့ `figure-` နဲ့စတဲ့ `img` တွေကို select လုပ်ချင်တယ်ဆိုရင်- 

    img[src|="figure"] {
        border: 1px solid gray;
    }

### `[foo~="bar"]` Examples
    <p class="urgent warning">....</p>

ဒီမှာ class attribute မှာ `warning` ပါတဲ့ element ကို select လုပ်မယ်ဆိုရင်

    p[class~="warning"] {
        ...
    }

`title` attribute မှာ `Figure` စာလုံး ပါတဲ့ `img`တွေကို border ထည့်မယ်ဆိုရင် 

    img[title~="Figure"] {
        border: 1px solid gray;
    }

သတိထားရမှာက `Figure` ဖြစ်မှ select လုပ်မှာဖြစ်ပြီး `figure` ဆိုရင် မလုပ်ပါဘူး။  <strong>case sensitive</strong> ဖြစ်ပါတယ်။  

[^1]: ဒီ note က [CSS: The Definitive Guide, 5th Edition by Eric Meyer, Estelle Weyl](https://www.oreilly.com/library/view/css-the-definitive/9781098117603/) စာအုပ်ကို refer လုပ်ထားတာဖြစ်ပြီး ၊ ကျွန်တော်ပြန်ဖတ်ဖို့ ကျွန်တော့ရဲ့ ကိုယ်ပိုင် study note တစ်ခုသာဖြစ်လို့ အမှားပါကောင်းပါနိုင်ပါတယ်။  page - 34
[^2]: page 35
[^2]: page 37