# Spread Operator and Shallow Copy

    let shuffledQuestions = [...questions];

## Spread Operator (`...`)
Spread operator က array, object စတဲ့ iterable လုပ်လို့ရတာတွေကို individual element တွေအဖြစ် expand လုပ်ပေးပါတယ်။  သူ့ကို array literal ထဲ `[...]` ထည့်သုံးရင် iterable လုပ်လို့ရတဲ့ element တွေကို new array ထဲထည့်ပေးပါတယ်။ [^1]

## Shallow Copy
အပေါ်ဆုံးက code example က spread operator ကိုသုံးပြီး `questions` array ကို shallow copy လုပ်တာပါ။  ဒီလိုလုပ်ခြင်းအားဖြင့် `shuffledQuestions` က `questions` ရဲ့ element တွေအားလုံးပါမှာဖြစ်ပြီး ကိုယ်ပိုင် structure ၊ ကိုယ်ပိုင် reference နဲ့ ရှိမှာပါ။  

    const originalArray = [1, 2, 3];
    const copiedArray = [...originalArray];

    console.log(originalArray); // Output: [1, 2, 3]
    console.log(copiedArray); // Output: [1, 2, 3]

    // Modifying the copied array does not affect the original array
    copiedArray.push(4);

    console.log(originalArray); // Output: [1, 2, 3]
    console.log(copiedArray); // Output: [1, 2, 3, 4]


Spread operator ကို မသုံးပဲ အောက်က code အတိုင်း assign လုပ်လိုက်ရင် `shuffledQuestions` array ရော `questions` array ပါ memory ထဲမှာ same array ကို point လုပ်နေမှာဖြစ်ပြီး array တစ်ခုမှာဖြစ်တဲ့ changes က နောက် array မှာပါလိုက်ဖြစ်နေမှာပါ။  

    let shuffledQuestions = questions;

## Deep vs. Shallow Copy
Spread operator က shallow copy လုပ်တယ်ဆိုတဲ့နေရာမှာ top-level element တွေကိုပဲ copy ကူးတာဖြစ်ပါတယ်။  အကယ်လို့ array မှာ object တွေ ၊ array တွေထပ်ပါနေအုံးမယ်ဆိုရင် အဲ့ဒီ nested element တွေကို copy ကူးမှာမဟုတ်ပဲ reference လုပ်သွားမှာဖြစ်တဲ့အတွက် nested object တွေ ၊ array တွေကို copy ကူးထားတဲ့ array မှာ ပြောင်းလိုက်ရင် origianl array မှာပါ လိုက်ပြောင်းသွားမှာပါ။  

    const originalArray = [{a: 1}, {b: 2}];
    const copiedArray = [...originalArray];

    copiedArray[0].a = 99;

    console.log(originalArray); // Output: [{a: 99}, {b: 2}]
    console.log(copiedArray); // Output: [{a: 99}, {b: 2}]

[^1]: အခုရေးထားတဲ့ spread operator နဲ့ shallow copy အကြောင်းကို ChatGPT က သင်ပေးထားတာပါ :sweat_smile: