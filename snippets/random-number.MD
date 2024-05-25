# Random Function
    function random(min, max) {
        return Math.floor(Math.random() * (max - min + 1)) + min;
    }

# Explanations

#### `Math.random()`
generates a floating-point random number between 0(inclusive) and 1 (exclusive).

---

#### `(max - min + 1)` -> range adjustment
`Math.random` က ထုတ်ပေးလိုက်တဲ့ 0 ကနေ 1 ကြားနံပါတ်ကို ကိုယ်လိုချင်တဲ့ `min`, `max` ကြားထဲရောက်ဖို့အတွက် range adjustment လုပ်ပေးထားတာပါ။ `Math.random` က ထုတ်ပေးတဲ့ နံပါတ်မှာ 1 က exclusive ဖြစ်နေတဲ့အတွက်ထုတ်ပေးတဲ့ နံပါတ်တွေမှာ 1 ပါလာဖို့ `+1` လုပ်ပေးရပါတယ်။ ဥပမာ - RBG number ကို random ထုတ်ချင်လို့ range ကို `max = 255`, `min = 0` ပေးလိုက်ရင် 255 က exclusive ဖြစ်နေတဲ့အတွက် ထုတ်တဲ့ နံပါတ်တိုင်းမှာ 255 ပါလာမှာ မဟုတ်ပါဘူး။ ဒါကြောင့် `+1` က လိုအပ်ပါတယ်။ 

---

#### `Math.random() * (max - min + 1)` -> multiplication by range
ထုတ်ပေးတဲ့ random number ကို desired range ထဲ ဝင်ဖို့ ဒီ expression က လုပ်ပေးပါတယ်။

---

#### `Math.floor()` -> flooring
ရလာတဲ့ result ကို nearest integer ဖြစ်အောင် round လုပ်ပေးပါတယ်။ 

---

#### `Math.floor(...) + min`  -> offsetting
ရလာတဲ့ နောက်ဆုံး result ဟာ min ကနေ စဖို့အတွက် min ကို add လုပ်ပေးတာပါ။  ဥပမာ - random number ကို 5 က စချင်လို့ min = 5 သတ်မှတ်ထားပေမယ့် ဒီအဆင့် မရောက်ခင်အထိ တွက်ထားတဲ့ result က 0 ကနေ စနေတာဖြစ်ပါတယ်။ ဒါကြောင့် လိုချင်တဲ့ min က စဖို့အတွက် နောက်ဆုံးအဆင့်မှာ min ကို add လုပ်ပြီး offset လုပ်ပေးဖို့ လိုပါတယ်။

# Usage
    function randomRGB() {
      return `rgb(${random(0, 255)},${random(0, 255)},${random(0, 255)})`;
    }