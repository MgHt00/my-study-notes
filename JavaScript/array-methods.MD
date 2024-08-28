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

### General Features
Iterator methods အားလုံးက
- source array ကို iterate လုပ်ပြီး
- source array ကို alteration/modify <strong><em>မလုပ်</em></strong> ပါဘူး

## Summary Table
|forEach() | map() | filter() | find() and findIndex() | every() and some() | reduce() and reduceRight() |
| --- | --- | --- | --- | --- | --- |
| no return |return an array | return an array | return a value | returns true/false | returns a reduced value |
|<em>Needs</em>|
| --- | ( ) should return a value | ( ) should return true/false | ( ) should return true/false | ( ) should return true/false | ( ) w or w/o initial value<br><br> |
| <em>Features</em>  |
| <li>iterate through an array, invoking a () specified </li><br><br><br> | <li>will not call ( ) for the sparse elements</li><li>but return sparse</li><br> | <li>skips sparse element</li><li>returns dense array</li><br><br>| <li>stops iterate when the element is found</li><br><br><br><br> | <li>`every` stops when false is found;</li> <li>`some` stops when true is found</li> | <li>to combine/ reduce into a single value</li><br><br><br><br><br> |

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

## find() and findIndex()[^5]
Array ကို iterate လုပ်ပြီး လိုချင်တဲ့ element ကို ရှာတွေ့တာနဲ့ ရပ်မှာပါ။ `find()` က matching element ကို return လုပ်ပြီး `findIndex()` က matching element ရဲ့ index ကို return လုပ်ပါတယ်။ 

ရှာမတွေ့ရင် `find()` က `undefined`, `findIndex()` က `-1` return ပါတယ်။

        let a = [1,2,3,4,5];
        a.findIndex(x => x === 3); // => 2
        a.findIndex(x => x < 0 ); // => -1
        a.find(x => x % 5 === 0); // => 5
        a.find(x => x % 7 === 0); // => undefined

## every() and some()[^6]

| every() | some() |
| --- | -- |
| all element ကို စစ်လို့ အားလုံး `true` ဖြစ်နေရင် `true` return ပါတယ်။ | အနည်းဆုံး element တစ်ခု `true` ဖြစ်ရင် `true` return ပါတယ်။  |
| empty array ကို invoke လုပ်ရင် `true` return ပါတယ် | empty array ကို invoke လုပ်ရင် `false` return ပါတယ်။ |

Explicit loop မရေးပဲ array ကို check လုပ်ဖို့အတွက် ဒီ method ၂ ခုက အသုံးတည့်ပါတယ်။[^7]

## reduce() and reduceRight()[^8]
ပေးထားတဲ့ function ကို သုံးပြီး array ရဲ့ element တွေကို combine လုပ်ပြီး single value ထုတ်ပေးပါတယ်။

`reduce()` က argument ၂ ခုယူပြီး ပထမက function, ဒုတိယက optional ဖြစ်ပြီး function ကို pass မယ့် initial value ပါ။  function ရဲ့ အလုပ်က value ၂ ခုကို ပေါင်း ၊ ဒါမှမဟုတ် single value ဖြစ်အောင် reduce လုပ်ပြီး reduced value ကို return လုပ်ပါတယ်။

ဒီမှာ `forEach()` တို့ `map()` တို့နဲ့ကွာတာက

        forEach(function(value, index, array)); 

        reduce(function(accumulator, value, index, array));

### Accumulator 
<em>First call to the function</em> - function ကို ပထမဆုံး ခေါ်တဲ့အချိန်မှာ initial value ပေးထားရင် initial value ကို accumulator အနေနဲ့ သုံးပြီး ၊ inital value မပေးထားရင် array ရဲ့ first element ကို accumulator အနေနဲ့ သုံးပါတယ်။  

<em>Subsequent calls</em>- ခုချိန်မတိုင်ခင်အကြိမ်မှာ function ကို invoke လုပ်ရထားတဲ့ result ပါ။  

        let a = [1,2,3,4,5];
        a.reduce((x,y) => x+y, 0); 
        // => 15; 0 က () မှာစသုံးရမယ့် initial valueပါ။
        // x က inital value/accumulator ဖြစ်ပြီး y က array ရဲ့ value ပါ။  

        a.reduce((x,y) => x*y, 1);
        // => 120; initial value ကို 0 ပေးထားခဲ့ရင် အဖြေက 0 ထွက်မှာပါ။
    
ဒီအောက်က snippet က initial value မပေးပဲထားတာကြောင့် first call မှာ x က array ရဲ့ first element => 1 ကို ယူပါတယ်။  first call မှာ (1 > 2) ပါ။ condition က false ဖြစ်တာကြောင့် 2 ကို return ပြန်ပြီး နောက်တစ်ကြိမ် invoke လုပ်တဲ့အခါ x => 2, y က 3 ပါ။  

        a.reduce((x,y) => (x > y) ? x : y);
        // => 5; x = value က, y = index ထဲ ကြီးနေရင် value ကို return ပြန်ပြီး ရှေ့ဆက်

Empty array မှာ inital value မပေးပဲ `reduce()` ကို call ရင် `TypeError` ထွက်ပါတယ်။  

One value - 1 element ပဲ ရှိတဲ့ array ကို initial value မပေးပဲ ၊ ဒါမှမဟုတ် empty array ကို initial value ပေးပြီးဖြစ်ဖြစ် `reduce()` ကို call ရင် reduction function ကို call မလုပ်တော့ပဲ အဲ့ဒီ one value ကိုပဲ return ပြန်ပါတယ်။ 

### reduceRight()
`reduceRight()` က အားလုံးတူပြီး သူက highest index to lowest index (right-to-left) process လုပ်မှာပါ။

### Second Argument

        every(function(element, index, array), thisArgument);

တခြား iterator method တွေမှာ `this` value ကို specify လုပ်မယ့်  optional argument ကို specify လုပ်လို့ ရပေမယ့် `reduce()` နဲ့ `reduceRight()` မှာတော့ optional second argument နေရာကို initial value ကယူလိုက်ပြီးပြီ ဖြစ်တာကြောင့် ထပ်ပြီး pass လုပ်လို့မရတော့ပါဘူး။  

### Special Feature
Two value(such as two objects) ကို one value of the same type အဖြစ် combine လုပ်နိုင်တဲ့ ဘယ် function ကို မဆို `reduce()` နဲ့ `reduceRight()` မှာသုံးလို့ ရပါတယ်။  (အခြား iterator methods တွေကတော့ mathematical computation ပဲလုပ်နိုင်ပါတယ်။)

[^1]: ဒီ note က ([CSS: The Definitive Guide, 5th Edition by Eric Meyer, Estelle Weyl](https://www.oreilly.com/library/view/css-the-definitive/9781098117603/)) စာအုပ်ကို refer လုပ်ထားတာဖြစ်ပြီး ၊ ကျွန်တော်ပြန်ဖတ်ဖို့ ကျွန်တော့ရဲ့ ကိုယ်ပိုင် study note တစ်ခုသာဖြစ်လို့ အမှားပါကောင်းပါနိုင်ပါတယ်။  
[^2]: page 166
[^3]: page 166
[^4]: page 167
[^5]: page 167
[^6]: page 167
[^7]: ChatGPT
[^8]: page 168