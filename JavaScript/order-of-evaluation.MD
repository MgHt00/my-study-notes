# Order of Evaluation

Expression တစ်ခုကို ဘယ် order နဲ့ operate လုပ်မယ်ဆိုတဲ့ order of operation ကို operator precedence နဲ့ associativity က သတ်မှတ်ပေမယ့် ၊ sub-expression တွေကို ဘယ်လို evaluate လုပ်မယ်ဆိုတဲ့ order ကိုတော့ မသတ်မှတ်ပါဘူး။ [^1]

**Javascript က expression  တွေကို အစဥ်ထာဝရ left-to-right order နဲ့ strictly evaluate လုပ်ပါတယ်။**

w = x + y * z ဆိုတဲ့ expression ကို အခုလောလောဆယ် ကျွန်တော်နားလည်ထားတာက ဒီလိုပါ။  

![subexpression explanation](https://github.com/MgHt00/my-study-notes/blob/15d41137775bcaed8e519ecdce31be9bb2527a55/JavaScript/_assets/subexpressions.webp?raw=true)

ဒီ expression မှာ subexpression ဖြစ်တဲ့ w ကို အရင် evaluate လုပ်ပြီးမှ x, y နဲ့ ကိစ္စကို evaluate လုပ်မှာပါ။

Multiplication, addition, နဲ့ assignment လုပ်တဲ့ order ကို ( ) parentheses ထည့်ပြီး ပြောင်းလို့ရပေမယ့် left-to-right order of evaluation ကိုတော့ ပြောင်းလို့ မရပါဘူး။ 

## Evaluate [^2]
To "evaluate" an expression means to compute its value.

## 1. Evaluating Variables and Constants
JavaScript engine အနေနဲ့ variable သို့မဟုတ် constant တစ်ခုကို တွေ့ပြီဆိုရင် သူ့ကို "evaluate" လုပ်ပြီး သူ့ရဲ့ current value ကို memory ထဲကနေ ဆွဲထုတ်ပါတယ်။

    let x = 2;
    let y = 3;

    // Evaluation
    x; // Evaluates to 2
    y; // Evaluates to 3

## 2. Evaluating Expressions
Expression တစ်ခုဆိုတာ value တစ်ခုကို ထုတ်ပေးနိုင်တဲ့ unit of code ပါ။  Expression ကို "evaluate" လုပ်တယ်ဆိုတာ language (JavaScript) ရဲ့ rule တွေကို အခြေခံပြီး value ကို compute လုပ်တာပါ။  

    let a = 5 + 3;

    // Evaluation steps:
    5 + 3; // Evaluates to 8

    let b = a * 2;

    // Evaluation steps:
    a * 2; // Evaluates to 8 * 2, which is 16

## 3. Evaluating Functions
Function တစ်ခုကို call လုပ်ပြီဆိုရင် "evaluate" အဆင့်က function ရဲ့ body ကို execute လုပ်ပြီး value တစ်ခုကို return လုပ်ပေးပါတယ်။

    function getValue() {
    return 42;
    }

    // Evaluation
    getValue(); // Evaluates to 42

## 4. Sub-expressions and Evaluation Order
Complex expression တွေ - multiple sub-expression တွေရှိတဲ့ အခြေအနေမှာ sub-expression တိုင်းကို "evaluate" လုပ်ပေးရပါတယ်။

    let x = 2;
    let y = 3;
    let z = 4;

    let result = x + y * z;

ဒီမှာ `x`, `y` နဲ့ `z` တွေက sub-expression တွေပါ။  ဒါကြောင့် result ကို "evaluate" လုပ်တဲ့အခါ ၊ JavaScript က

1. `x` ကို evaluate လုပ်ပြီး `2` ထုတ်ပါတယ်။
2. `y` ကို evaluate လုပ်ပြီး `3` ထုတ်ပါတယ်။
3. `z` ကို evaluate လုပ်ပြီး `4` ထုတ်ပါတယ်။
4. `y * z` ကို evaluate လုပ်ပြီး `12` ထုတ်ပါတယ်။ (operator precedence အရ `*` ကို `+` ထက်အရင် evaluate လုပ်ပါတယ်။)
5. `x + 12` ကို evaluate လုပ်ပြီး `14` ထုတ်ပါတယ်။

## 5. Left-to-Right Evaluation
Operator precedence က order of operations ကို သတ်မှတ်ပေးပေမယ့် JavaScript ကတော့ sub-expression တိုင်းကို left to right ပဲ evaluate လုပ်ပါတယ်။ 

    function getX() {
    console.log('Evaluating x');
    return 2;
    }

    function getY() {
        console.log('Evaluating y');
        return 3;
    }

    function getZ() {
        console.log('Evaluating z');
        return 4;
    }

    let result = getX() + getY() * getZ();
    
ဒီ snippet မှာ 

1. `getX()` ကို အရင် evaluate လုပ်၊ "Evaluating x" ကို log လုပ်ပြီး 2 return ပြန်ပါတယ်။
2. `getY()` ကို ဒုတိယ evaluate လုပ်၊ "Evaluating y" ကို log လုပ်ပြီး 3 return ပြန်ပါတယ်။
3. `getZ()` ကို တတိယ evaluate လုပ်၊ "Evaluating z" ကို log လုပ်ပြီး 4 return ပြန်ပါတယ်။
4. ပြီးမှ `getY() * getZ()` ကို evaluate လုပ်လို့  3 * 4 = 12 ထွက်ပါတယ်။ (* ရဲ့ higher precedence ကြောင့် * ကို အရင် evaluate လုပ်တာပါ။)
5. နောက်ဆုံးမှ `getX() + 12` ကို evaluate လုပ်ပြီး 2 + 12 = 14 ထွက်ပါတယ်။ 

# Evaluation Order of Sub-Expressions
Key point က operator precedence and associativity က ဘယ် <strong>operations</strong> ကို အရင် perform လုပ်မယ်ဆိုတာ သတ်မှတ်ပေးပေမယ့် <strong>sub-expression</strong> (individual component) တွေ ဘယ် order နဲ့ evaluate လုပ်မယ်ဆိုတာကိုတော့ မသတ်မှတ်ပေးပါဘူး။  JavaScript က expression တွေကို left to right ပဲ evaluate လုပ်ပါတယ်။ 

    w = x + y * z

1. Step 1: Evaluate w (the target of the assignment).
2. Step 2: Evaluate x.
3. Step 3: Evaluate y.
4. Step 4: Evaluate z.
5. Step 5: Compute y * z (due to higher precedence of *).
6. Step 6: Compute x + (y * z).
7. Step 7: Assign the result to w.



[^1]: ဒီ post က ကျွန်တော်ပြန်ဖတ်ဖို့ ကျွန်တော့ရဲ့ ကိုယ်ပိုင် note တစ်ခုသာဖြစ်ပြီး [JavaScript: The Definitive Guide, 7th Edition by David Flanagan](https://www.oreilly.com/library/view/javascript-the-definitive/9781491952016/) စာအုပ်ကို refer လုပ်ထားပါတယ်ဗျာ။ 

[^2]: ChatGPT - GPT-4o