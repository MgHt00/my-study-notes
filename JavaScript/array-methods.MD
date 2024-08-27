# Array Methods[^1]
- Iterator methods - array ရဲ့ elements တွေပေါ် specify လုပ်ထားတဲ့ function အတိုင်း loop လုပ်ပါတယ်.
- Stack and queue methods - array ရဲ့ အစ ၊ အဆုံး မှာ element တွေ add, remove လုပ်ပါတယ်။
- Subarray methods - larger array ရဲ့ contiguous region တွေကို extract, delete, insert, fill, and copy လုပ်ဖို့ သုံးပါတယ်။
- Searching and sorting methods - array ထဲမှာ  element တွေ locate လုပ်ဖို့ ၊​ sort လုပ်ဖို့ သုံးပါတယ်။ 

# Array Iterator Methods
ဒီ method တွေက array ရဲ့ element တွေကို supply လုပ်ထားတဲ့ function ဆီ pass လုပ်ပါတယ်။ iterate, map, filter, test, and reduce လုပ်ဖို့ အသုံးတည့်ပါတယ်။

ဒီ method တွေက function ကို first argument အနေနဲ့ accept လုပ်ပြီး element တစ်ခုချင်းအပေါ် invoke လုပ်ပါတယ်။ Array က sparse ဖြစ်နေရင် မရှိတဲ့ element တွေအတွက် function invoke မလုပ်ပါဘူး။ First argument - function အတွက် 

- value of the array element,
- index of the array element, 
- array itself 

ဒီ argument ၃ ခု pass လုပ်လို့ရပေမယ့် များသောအားဖြင့် 1st arguement (value of the array element) ပဲ လိုအပ်တာများပါတယ်။ 

ဒီ method တွေကို optional second argument pass လုပ်လို့ ရပြီး pass လုပ်ရင် first argument ဖြစ်တဲ့ function က second argument ရဲ့ method အလား အလုပ်ပါတယ်။

Second argument က first argument - function မှာ သုံးထားတဲ့ `this` keyword ရဲ့ value ဖြစ်လာပါတယ်။

## Summary Table
|forEach() | map() | filter() | find() and findIndex() | every() and some() | reduce() and reduceRight() |
| --- | --- | --- | --- | --- | --- |
| <li>no return</li><li>no alteration</li> |<li>return an array</li><li>no alteration</li> | <li>return an array</li><li>no alteration</li> | --- | --- | --- |
| Needs|
| --- | ( ) should return a value | ( ) should return true/flase | --- | --- | --- |
| Features | --- | --- | --- | --- | --- |
| --- | <li>will not call ( ) for the sparse elements</li><li>but return sparse</li> | <li>skips sparse element</li><li>returns dense array</li> | --- | --- | --- |
| --- | --- | --- | --- | --- | --- |


## forEach()[^2]
First argument ဖြစ်တဲ့ function ကို argument ၃ ခု pass လုပ်လို့ ရသလို ၊ value ၁ ခုပဲ pass လုပ်လဲရပါတယ်။

    let data = [1,2,3,4,5];
    let sum = 0;

    data.forEach(value => {sum + value}); // sum == 15

    data.forEach(v, i, a => a[i] = v + 1); // data == [2,3,4,5,6]

`forEach()` မှာ `break` ပေးပြီး iteration ကို terminate လုပ်လို့မရပဲ array ဆုံးတဲ့ထိ သွားမှာပါ။ 

## map()[^3]
Pass လုပ်လိုက်တဲ့ function က return ပြန်တဲ့ value ပါတဲ့ array ကို return ပြန်ပါတယ်။

    let a = [1,2,3];
    a.map(x => x*x); // => [1,4,9]

`map()` အတွင်းမှာ pass လုပ်တဲ့ function က return ပြန်သင့်ပါတယ်။ 

`map()` က new array ကို return ပြန်ပြီး function invoke လုပ်တဲ့ array ကို modify မလုပ်ပါဘူး​။

Array က sparse ဆိုရင် missing element တွေအတွက် function ကို call လုပ်မှာမဟုတ်ပေမယ့် return ပြန်တဲ့ array မှာတော့ original array အတိုင်း sparse လုပ်ထားမှာဖြစ်တာကြောင့် original array အတိုင်း same length ဖြစ်ပြီး same missing element တွေပါပါလိမ့်မယ်။

## filter()[^4]
Invoke လုပ်ခံရတဲ့ array ရဲ့ element အချို့ (subset) ပါတဲ့ array ကို return ပြန်ပါတယ်။ Pass လုပ်မယ့် function က `true`/`false` return ပြန်သင့်ပါတယ်။

Pass လုပ်ထားတဲ့ element ကို invoke လုပ်လို့ return value က `true` သို့မဟုတ် `true` ကို convert လုပ်နိုင်တဲ့ value ဖြစ်နေရင် အဲ့ဒီ element ကို function က return ပြန်မယ့် array ထဲမှာပါမယ့် element အဖြစ်သတ်မှတ်ပါတယ်။

    let a = [5,4,3,2,1];
    a.filter(x => x < 3);  // [2,1]

    a.filter((x,i) => i%2 === 0);  // [5,3,1]

`filter()` က sparse array တွေရဲ့ missing element တွေကို skip လုပ်ပြီး return value က always dense ဖြစ်ပါတယ်။  sparse တွေကို ဖျောက်ပြီး array ကို dense array ဖြစ်အောင် ပြောင်းချင်ရင် `filter()` ကို ဒီိလိုသုံးလို့ ရပါတယ်။

    let dense = sparse.filter(() => true); 
    // An arrrow function that takes no paramenters always returns `true`

Gap တွေကိုလဲ ဖျောက်မယ် ၊ undefined နဲ့ null တွေကိုလဲ ဖယ်ပစ်မယ်ဆိုရင် - 

    a = a.filter(x => x !== undefined && x !== null);

[^1]: ဒီ note က ([CSS: The Definitive Guide, 5th Edition by Eric Meyer, Estelle Weyl](https://www.oreilly.com/library/view/css-the-definitive/9781098117603/)) စာအုပ်ကို refer လုပ်ထားတာဖြစ်ပြီး ၊ ကျွန်တော်ပြန်ဖတ်ဖို့ ကျွန်တော့ရဲ့ ကိုယ်ပိုင် study note တစ်ခုသာဖြစ်လို့ အမှားပါကောင်းပါနိုင်ပါတယ်။  
[^2]: page 166
[^3]: page 166
[^4]: page 167