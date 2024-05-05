# Order of Evaluation

Expression တစ်ခုကို ဘယ် order နဲ့ operate လုပ်မယ်ဆိုတဲ့ order of operation ကို operator precedence နဲ့ associativity က သတ်မှတ်ပေမယ့် ၊ sub-expression တွေကို ဘယ်လို evaluate လုပ်မယ်ဆိုတဲ့ order ကိုတော့ မသတ်မှတ်ပါဘူး။ [^1]

**Javascript က expression  တွေကို အစဥ်ထာဝရ left-to-right order နဲ့ strictly evaluate လုပ်ပါတယ်။**

w = x + y * z ဆိုတဲ့ expression ကို အခုလောလောဆယ် ကျွန်တော်နားလည်ထားတာက ဒီလိုပါ။  

![subexpression explanation](https://github.com/MgHt00/my-study-notes/blob/15d41137775bcaed8e519ecdce31be9bb2527a55/JavaScript/_assets/subexpressions.webp?raw=true)

ဒီ expression မှာ subexpression ဖြစ်တဲ့ w ကို အရင် evaluate လုပ်ပြီးမှ x, y နဲ့ ကိစ္စကို evaluate လုပ်မှာပါ။

Multiplication, addition, နဲ့ assignment လုပ်တဲ့ order ကို ( ) parentheses ထည့်ပြီး ပြောင်းလို့ရပေမယ့် left-to-right order of evaluation ကိုတော့ ပြောင်းလို့ မရပါဘူး။ 

ပိုရှင်းမလားလို့ ChatGPT မှာ တီးခေါက်ကြည့်တော့ -

> Note that operator precedence and associativity only affect the order of evaluation of operators (the implicit grouping), but not the order of evaluation of operands.

တခါတလေတော့လဲ ရှင်းလေ ရှုပ်လေ :P

[^1]: ဒီ post က ကျွန်တော်ပြန်ဖတ်ဖို့ ကျွန်တော့ရဲ့ ကိုယ်ပိုင် note တစ်ခုသာဖြစ်ပြီး [JavaScript: The Definitive Guide, 7th Edition by David Flanagan](https://www.oreilly.com/library/view/javascript-the-definitive/9781491952016/) စာအုပ်ကို refer လုပ်ထားပါတယ်ဗျာ။ 