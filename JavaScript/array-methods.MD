# Array Methods[^1]
- Iterator methods - array ရဲ့ elements တွေပေါ် specify လုပ်ထားတဲ့ function အတိုင်း loop လုပ်ပါတယ်.
- Stack and queue methods - array ရဲ့ အစ ၊ အဆုံး မှာ element တွေ add, remove လုပ်ပါတယ်။
- Subarray methods - larger array ရဲ့ contiguous region တွေကို extract, delete, insert, fill, and copy လုပ်ဖို့ သုံးပါတယ်။
- Searching and sorting methods - array ထဲမှာ  element တွေ locate လုပ်ဖို့ ၊​ sort လုပ်ဖို့ သုံးပါတယ်။ 

| Category      | Sub-category |
| ----------- | ----------- |
| Array Iterator Methods | [Summary Table](#summary-table),  [forEach()](#11-foreach-2), [map()](#12-map-3), [filter()](#13-filter-4), [find() and findIndex()](#14-find--and-findindex-5), [every() and some()](#15-every--and-some-6), [reduce() and reduceRight()](#16-reduce--and-reduceright-8), [flat()](#17-flattening-arrays-with-flat--and-flatmap-9), [flatMap()](#17-flattening-arrays-with-flat--and-flatmap-9), [concat()](#18-adding-arrays-with-concat-12)  |
| Stack and queue methods | [push( ) and pop( )](#21-push--and-pop-), [shift( ) and unshift( )](#22-shift--and-unshift-) |
| Subarray methods | [Summary Table](#3-subarrays-with-slice--splice---fill---and-copywithin-15), [slice( )](#31-slice-), [splice( )](#32-splice-), [fill( )](https://github.com/MgHt00/my-study-notes/blob/main/JavaScript/array-methods.MD#33-fill-), [copyWithin( )](#34-copywithin-) |
| Searching and sorting methods | [Summary Table](#4-array-searching-and-sorting-methods16), [indexOf( ) and lastIndexOf( )](#41-indexof--and-lastindexof-), [includes( )](#42-includes-), [sort( )](#43-sort-), [reverse( )](#44-reverse-) |

# 1. Array Iterator Methods
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
|forEach() | map() | filter() | find() and findIndex() | every() and some() | reduce() and reduceRight() | flat() | flatMap() | concat() |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| no return |return an array | return an array (subset of the array on which it is invoked) | return a value | returns true/false | returns a reduced value | returns a flatten array | returns a flatten array | concatenate array elements |
|<em>Needs</em>|
| --- | ( ) should return a value | ( ) should return true/false | ( ) should return true/false | ( ) should return true/false | ( ) w or w/o initial value | does not use a callback ( ) | ( ) should return an iterable | does not use a callback ( )|
| <em>Features</em>  |
| <li>iterate through an array, invoking a () specified </li><br><br><br> | <li>will not call ( ) for the sparse elements</li><li>but return sparse</li><br> | <li>skips sparse element</li><li>returns dense array</li><br><br>| <li>stops iterate when the element is found</li><br><br><br><br> | <li>`every` stops when false is found;</li> <li>`some` stops when true is found</li> | <li>to combine/ reduce into a single value</li><br><br><br><br> | <li>elements that are themselves arrays are flattened into the returned array.</li> | <li>same as (but more efficient than)`a.map().flat()`</li><li>elements that are themselves arrays are flattened into the returned array.</li> |<li>returns a new array containing elements of the original array and the argument(s)</li> |

## 1.1 forEach( )[^2]
First argument ဖြစ်တဲ့ function ကို argument ၃ ခု pass လုပ်လို့ ရသလို ၊ value ၁ ခုပဲ pass လုပ်လဲရပါတယ်။

```javascript
    let data = [1,2,3,4,5];
    let sum = 0;

    data.forEach(value => {sum + value}); // sum == 15

    data.forEach((v, i, a) => a[i] = v + 1); // data == [2,3,4,5,6]
```
`forEach()` မှာ `break` ပေးပြီး iteration ကို terminate လုပ်လို့မရပဲ array ဆုံးတဲ့ထိ သွားမှာပါ။ 

## 1.2 map( )[^3]
Pass လုပ်လိုက်တဲ့ function က return ပြန်လာတဲ့ value ပါတဲ့ array ကို return ပြန်ပါတယ်။

```javascript
    let a = [1,2,3];
    a.map(x => x*x); // => [1,4,9]
```
`map()` အတွင်းမှာ pass လုပ်တဲ့ function က return ပြန်သင့်ပါတယ်။ 

`map()` က new array ကို return ပြန်ပြီး function invoke လုပ်တဲ့ array ကို modify မလုပ်ပါဘူး​။

Array က sparse ဆိုရင် missing element တွေအတွက် function ကို call လုပ်မှာမဟုတ်ပေမယ့် return ပြန်တဲ့ array မှာတော့ original array အတိုင်း sparse လုပ်ထားမှာဖြစ်တာကြောင့် original array အတိုင်း same length ဖြစ်ပြီး same missing element တွေပါပါလိမ့်မယ်။
```javascript
// Create a sparse array
let sparseArray = [1, , 3]; // This array has a missing element at index 1

// Use map() on the sparse array
let result = sparseArray.map(x => x * 2);

console.log(result); // Output: [2, , 6]
```

## 1.3 filter( )[^4]
Invoke လုပ်ခံရတဲ့ array ရဲ့ element အချို့ (subset) ပါတဲ့ array ကို return ပြန်ပါတယ်။ Pass လုပ်မယ့် function က `true`/`false` return ပြန်သင့်ပါတယ်။

Pass လုပ်ထားတဲ့ element ကို invoke လုပ်လို့ return value က `true` သို့မဟုတ် `true` ကို convert လုပ်နိုင်တဲ့ value ဖြစ်နေရင် အဲ့ဒီ element ကို function က return ပြန်မယ့် array ထဲမှာပါမယ့် element အဖြစ်သတ်မှတ်ပါတယ်။

```javascript
    let a = [5,4,3,2,1];
    a.filter(x => x < 3);  // [2,1]

    a.filter((x,i) => i%2 === 0);  // [5,3,1]
```
`filter()` က sparse array တွေရဲ့ missing element တွေကို skip လုပ်ပြီး return value က always dense ဖြစ်ပါတယ်။  sparse တွေကို ဖျောက်ပြီး array ကို dense array ဖြစ်အောင် ပြောင်းချင်ရင် `filter()` ကို ဒီိလိုသုံးလို့ ရပါတယ်။

```javascript
    let dense = sparse.filter(() => true); 
    // An arrrow function that takes no paramenters always returns `true`
```
Gap တွေကိုလဲ ဖျောက်မယ် ၊ undefined နဲ့ null တွေကိုလဲ ဖယ်ပစ်မယ်ဆိုရင် - 

```javascript
    a = a.filter(x => x !== undefined && x !== null);
```
## 1.4 find( ) and findIndex( )[^5]
Array ကို iterate လုပ်ပြီး လိုချင်တဲ့ element ကို ရှာတွေ့တာနဲ့ ရပ်မှာပါ။ `find()` က matching element ကို return လုပ်ပြီး `findIndex()` က matching element ရဲ့ index ကို return လုပ်ပါတယ်။ 

ရှာမတွေ့ရင် `find()` က `undefined`, `findIndex()` က `-1` return ပါတယ်။

```javascript
        let a = [1,2,3,4,5];
        a.findIndex(x => x === 3); // => 2
        a.findIndex(x => x < 0 ); // => -1
        a.find(x => x % 5 === 0); // => 5
        a.find(x => x % 7 === 0); // => undefined
```
## 1.5 every( ) and some( )[^6]

| every() | some() |
| --- | -- |
| all element ကို စစ်လို့ အားလုံး `true` ဖြစ်နေရင် `true` return ပါတယ်။ | အနည်းဆုံး element တစ်ခု `true` ဖြစ်ရင် `true` return ပါတယ်။  |
| empty array ကို invoke လုပ်ရင် `true` return ပါတယ် | empty array ကို invoke လုပ်ရင် `false` return ပါတယ်။ |

Explicit loop မရေးပဲ array ကို check လုပ်ဖို့အတွက် ဒီ method ၂ ခုက အသုံးတည့်ပါတယ်။[^7]

## 1.6 reduce( ) and reduceRight( )[^8]
ပေးထားတဲ့ function ကို သုံးပြီး array ရဲ့ element တွေကို combine လုပ်ပြီး single value ထုတ်ပေးပါတယ်။

`reduce()` က argument ၂ ခုယူပြီး ပထမက function, ဒုတိယက optional ဖြစ်ပြီး function ကို pass မယ့် initial value ပါ။  function ရဲ့ အလုပ်က value ၂ ခုကို ပေါင်း ၊ ဒါမှမဟုတ် single value ဖြစ်အောင် reduce လုပ်ပြီး reduced value ကို return လုပ်ပါတယ်။

ဒီမှာ `forEach()` တို့ `map()` တို့နဲ့ကွာတာက

```javascript
        forEach(function(value, index, array), value of this keyword); 

        reduce(function(accumulator, value, index, array), initial value);
```
### Accumulator 
<em>First call to the function</em> - function ကို ပထမဆုံး ခေါ်တဲ့အချိန်မှာ initial value ပေးထားရင် initial value ကို accumulator အနေနဲ့ သုံးပြီး ၊ inital value မပေးထားရင် array ရဲ့ first element ကို accumulator အနေနဲ့ သုံးပါတယ်။  

<em>Subsequent calls</em>- ခုချိန်မတိုင်ခင်အကြိမ်မှာ function ကို invoke လုပ်ရထားတဲ့ result ပါ။  

```javascript
        let a = [1,2,3,4,5];
        a.reduce((x,y) => x+y, 0); 
        // => 15; 0 က () မှာစသုံးရမယ့် initial valueပါ။
        // x က inital value/accumulator ဖြစ်ပြီး y က array ရဲ့ value ပါ။  

        a.reduce((x,y) => x*y, 1);
        // => 120; initial value ကို 0 ပေးထားခဲ့ရင် အဖြေက 0 ထွက်မှာပါ။
``` 
ဒီအောက်က snippet က initial value မပေးပဲထားတာကြောင့် first call မှာ x က array ရဲ့ first element => 1 ကို ယူပါတယ်။  first call မှာ (1 > 2) ပါ။ condition က false ဖြစ်တာကြောင့် 2 ကို return ပြန်ပြီး နောက်တစ်ကြိမ် invoke လုပ်တဲ့အခါ x => 2, y က 3 ပါ။  

```javascript
        a.reduce((x,y) => (x > y) ? x : y);
        // => 5; x = value က, y = index ထဲ ကြီးနေရင် value ကို return ပြန်ပြီး ရှေ့ဆက်
```
Empty array မှာ inital value မပေးပဲ `reduce()` ကို call ရင် `TypeError` ထွက်ပါတယ်။  

One value (one element) ပဲ ရှိတဲ့ array ကို initial value မပေးပဲ ၊ ဒါမှမဟုတ် empty array ကို initial value ပေးပြီးဖြစ်ဖြစ် `reduce()` ကို call ရင် reduction function ကို call မလုပ်တော့ပဲ အဲ့ဒီ one value ကိုပဲ return ပြန်ပါတယ်။ 

### reduceRight( )
`reduceRight()` က အားလုံးတူပြီး သူက highest index to lowest index (right-to-left) process လုပ်မှာပါ။

### Second Argument

        every(function(element, index, array), thisArgument);

တခြား iterator method တွေမှာ `this` value ကို specify လုပ်မယ့်  optional argument ကို specify လုပ်လို့ ရပေမယ့် `reduce()` နဲ့ `reduceRight()` မှာတော့ optional second argument နေရာကို initial value ကယူလိုက်ပြီးပြီ ဖြစ်တာကြောင့် ထပ်ပြီး pass လုပ်လို့မရတော့ပါဘူး။  

### Special Feature
Two value(such as two objects) ကို one value of the same type အဖြစ် combine လုပ်နိုင်တဲ့ ဘယ် function ကို မဆို `reduce()` နဲ့ `reduceRight()` မှာသုံးလို့ ရပါတယ်။  (အခြား iterator methods တွေကတော့ mathematical computation ပဲလုပ်နိုင်ပါတယ်။)

## 1.7 Flattening arrays with flat( ) and flatMap( )[^9]
`flat()` က ပေးလိုက်တဲ့ array ကို pass လုပ်လိုက်တဲ့ argument အတိုင်း flat လုပ်ပြီး နဂိုပါတဲ့ element တွေ အားလုံး နဂို value အတိုင်း(flat လုပ်ပြီး) ပြန်ပါတဲ့ array ကို return လုပ်ပေးပါတယ်။ 

```javascript
        let a = [1, [2, [3, [4]]]];
        a.flat(1); // => [1, 2, [3, [4]]]
        a.flat(2); // => [1, 2, 3, [4]]
        a.flat(3); // => [1, 2, 3, 4]
        a.flat(4); // => [1, 2, 3, 4]
        a.flat(infinity); // => [1, 2, 3, 4]
```
`flatMap()` ကတော့ ပေးလိုက်တဲ့ array element တွေကို `map()` အရင်လုပ် ၊ ပြီးမှ `flat()` ထပ်လုပ်ပြီး array ကို return လုပ်ပါတယ်။

```javascript
        let phrases = ["hello world", "the definitive guide"];
        let words = phrases.flatMap(phrase => phrase.split( ));
        words; // => ["hello", "world", "the", "definitive", "guide"]
```
|[^10]flat( )|flatMap( )|
|---|---|
|<strong>Usage: </strong>To flatten an array to a specified depth<br><br><strong>No callback: </strong>The method does not use a callback function. |<strong>Useage: </strong>To first map each element using a mapping function and then flatten the result into a new array.<br><br><strong>Callback required: </strong>The callback function is required and should return an iterable. |

#### Different Return Types in flatMap()
အကယ်လို့ flatMap() ရဲ့ callback function က return ပြန်လာတာက array သို့မဟုတ် iterate လုပ်လို့ မရတဲ့ value ဖြစ်နေရင် flatMap() က array တစ်ခုတည်း ထည့်ပေးပါတယ်။

```javascript
        let arr = [1,2,3,4];

        let flatMappedArr = arr.flatMap(x => x * 2); // => [2,4,6,8]
```
#### Important Points
- `flat()` က callback function မယူပါဘူး ၊ array ကို flatten လုပ်ရုံလုပ်ပေးပါတယ်။
- `flatMap()` မှာ callback function လိုအပ်ပြီး ၊ function ရဲ့ return value က array (သို့) iterable ဖြစ်သင့်ပါတယ်။
- `flatMap()` က `map()` operation ကိုအရင်လုပ်ပြီး `flat()` operation ကို depth of `1` နဲ့ ဆက်လုပ်ပါတယ်။ [^11]

## 1.8 Adding arrays with concat( )[^12]
Original array နဲ့ pass လုပ်လိုက်တဲ့ argument တစ်ခုချင်းကိုပေါင်းထားတဲ့ array အသစ်ကို return ပြန်ပေးပြီး original array ကိုတော့ မပြောင်းလဲပါဘူး။  Pass လုပ်ထားတဲ့ argument က array ဆိုရင် အဲ့ဒီ array ရဲ့ element တွေကိုဆွဲယူ ၊ concatenate လုပ်ပေးမှာဖြစ်ပြီး array တစ်ခုလုံးအနေနဲ့ concatenate လုပ်ပေးမှာမဟုတ်သလို ၊ arrays of arrays ကို argument အနေနဲ့ pass လုပ်လိုက်ရင်လဲ recursively flatten လုပ်မှာ မဟုတ်ပါဘူး။  

```javascript
        let a = [1,2,3];
        a.concat(4,5);          // => [1,2,3,4,5]
        a.concat([4,5], [6,7]); // => [1,2,3,4,5,6,7]
        a.concat(4, [5,[6,7]]); // => [1,2,3,4,5,[6,7]]
        a;                      // => [1,2,3]
```
# 2. Stacks and Queues with push( ), pop( ), shift( ), and unshift( )[^13]

|Beginning of the Array|End of the Array|
|---|---|
|<li>unshift( )</li><li>shift( )|<li>push( )</li><li>pop( )</li>|

### 2.1 push( ) and pop( )
`push( )` နဲ့ `pop( )` က array တွေကို stack တွေအလား အလုပ်လုပ်ပေးပါတယ်။ 

|push()|pop()|
|---|---|
|one of more element ကို end of the array မှာ append လုပ်ပါတယ်| array ရဲ့ last element ကို delete လုပ်ပါတယ်|
|array ရဲ့ length ကို increse လုပ်ပါတယ်| array ရဲ့ length ကို decrese လုပ်ပါတယ်|
|new length of the array ကို return ပြန်ပါတယ်|the value that it removed ကို return ပြန်ပါတယ်|
|modify the array in place| modify the array in place|
|argument မှာ array ကို pass လုပ်ရင် flattern မလုပ်ပေးပါဘူး (concat() နဲ့ ကွာပါတယ်။)|---|

```javascript
        let stack = [];
        stack.push(1,2);   // => stack == [1,2]
        stack.pop();       // => returns 2; stack == [1]

        stack.push([4,5]); // => stack == [1, [4,5]]
```
`push()` က array ကို flatten မလုပ်တာကြောင့် array မှာ ရှိတဲ့ all element ကို နောက် array ဆီ push ချင်ရင် spread oprator နဲ့ flatten လုပ်လို့ ရပါတယ်။

        a.push(...value);

### 2.2 shift( ) and unshift( )
ဒီ method ၂ ခုက beginning of the array မှာ အလုပ်လုပ်ပါတယ်။

|unshift( ) | shift ( )|
|---|---|
|Beginning of the array မှာ add လုပ်ပါတယ်|first element of the array ကို remove လုပ်ပါတယ်။|
|နေရာ ရှိလာအောင် existing element တွေကို higher index တစ်ခုဆီရွေ့ပါတယ်| လွတ်သွားတဲ့ နေရာကိုဖြည့်ဖို့ ကျန်တဲ့ element တွေကို one place ဆီ ချပါတယ်။|
|returns the new length of the array|remove လုပ်လိုက်တဲ့ first element ကို return ပြန်ပါတယ်။|

ဒီ method ၄ ခုကို သုံးပြီး stack and queue[^14] ဖြစ်အောင် အလုပ်လုပ်လို့ ရပါတယ်။ 

```javascript
        let q = [];
        q.push(1,2);    // => q == [1,2]
        q.shift()       // => q == [2]; returns 1

        q.push(3);      // => q == [2,3]
        q.shift();      // => q == [3]; returns 2
```
`unshift( )` မှာ မှတ်စရာက ဥပမာ `unshift(1); unshift(2);` ဆိုရင် `a = [2,1]` ဖြစ်ပေမယ့် ၊ `unshift(1,2);` ဆိုရင် `a == [1,2]` ဖြစ်ပါတယ်။

# 3. Subarrays with slice( ), splice ( ), fill ( ), and copyWithin( )[^15]

| slice( ) | splice( ) | fill ( ) | copyWithin( ) |
| --- | --- | --- | --- |
| <li>returns a subarray</li><li>does not modify the array</li> | <li>returns an array of the deleted elements</li><li>modify the array</li> | <li>modify the array</li><li>returned a modified array</li> | <li>modify the array</li><li>returned a modified array</li> | 
| <em>Features</em> |
| <li>returns a subarray</li> | <li>insert / remove elements from an array</li><li>or perform both operations at the same time</li><li>indexes are increased or decereased as necessary</li> | <li>set a specified value to an element (of subset) of an array</li> | <li>copies a slice of an array to a new position within the array</li> |

### 3.1 slice( )
Subarray(slice) ကို return ပြန်ပါတယ်။ start နဲ့ end ကို argument အနေနဲ့ pass လုပ်ရပြီး first argument ကနေ second argument မတိုင်ခင်အထိ return ပြန်ပေးပါတယ်။  Argument တစ်ခုတည်း pass လုပ်ရင်တော့ start ကနေ end of the array ကို return ပြန်ပါတယ်။

```javascript
        let a = [1,2,3,4,5]
        a.slice(0, 3); 
        // returns [1,2,3]; 
        // index 0 က inclusive, index 3 က exclusive ပါ။

Argument က negative ဆိုရင် array ရဲ့ length ကနေ နှုတ်ပြီး အလုပ်လုပ်ပါတယ်။  

        a.slice(1, -1); // returns [2,3,4]

        a.slice(-3, -2); // returns [3]
```
### 3.2 splice( )
Array ထဲ element တွေထည့်လို့ရတယ် ၊ ဖျက်လို့လဲ ရသလို ၊ ၂ မျိုးလုံးလဲ တစ်ပြိုင်တည်း လုပ်နိုင်ပါတယ်။

First argument က insert/delete စလုပ်မယ့် array position (index no.) ဖြစ်ပြီး ၊ second argument က <strong>no. of element / length</strong> (not an index no.)ပါ။  Second argument ကို omit လုပ်ထားရင် start element ကနေ end of the array ထိ remove လုပ်ပါမယ်။

`splice()` က array of the deleted elements ကို return ပြန်ပြီး ဘာ element ကိုမှ delete မလုပ်ရင် empty array ကို return ပြန်ပါတယ်။ 

```javascript
        let a = [1,2,3,4,5,6,7,8];
        a.splice(4);    // => returns [5,6,7,8]; a is now [1,2,3,4]
        a.splice(1,2);  // => returns [2,3]; a is now [1,4]
```
Argument က ၂ ခု မဟုတ်ပဲ နောက်မှာ ဆက်ပါလာရင် ဖျက်လဲဖျက်မယ် ၊ insert လဲ လုပ်ပါမယ်။  

```javascript
        let a = [1,2,3,4,5];
        
        a.splice(2,0,"a","b");  
        // => returns []; no element is deleted;
        // => a is now [1,2,"a","b",3,4,5]

        a.splice(2,2,[1,2],3)
        // => returns ["a","b"]
        // => a is now [1,2,[1,2],3,3,4,5]
```
Note: `concat()` က array ရဲ့ element ကို insert လုပ်ပြီး ၊ `splice` က array ကို array အတိုင်း insert လုပ်ပါတယ်။ 

### 3.3 fill( )
Array ရဲ့ element (သို့) တစ်စိတ်တစ်ပိုင်းကို သတ်မှတ်ပေးလိုက်တဲ့ value နဲ့ set(fill) လုပ်ပေးပါတယ်။  Array ကို directly modify (mutate) လုပ်ပြီး modified array ကို return ပြန်ပါတယ်။

First argument က set(fill) လုပ်မယ့် value ပါ။  

Optional second argument က index no. ဖြစ်ပြီး သူ့မတိုင်ခင်ထိ set(fill) ပါတယ်။  Second argument မပါရင် end of the array ထိ သွားပြီး ၊ negative value ပေးရင် array ရဲ့ length ထဲက နှုတ်ပါတယ်။  

```javascript
        let a = new Array(5);   // => start with no elements and length of 5
        a.fill(0);              // => returns [0,0,0,0,0]
        a.fill(9,1);            // => returns [0,9,9,9,9]
        a.fill(8, 2, -1);       // => returns [0,9,8,8,9]
```

### 3.4 copyWithin( )
Slice of an array ကို same array ရဲ့ new position ဆီ copy လုပ်ပေးပါတယ်။ Array ကို in place မှာပဲ modify လုပ်ပြီး modified array ကို return ပြန်ပါတယ်။ 

Length of the array က အပြောင်းအလဲ မရှိပါဘူး။

- First argument - copy လုပ်ထားတဲ့ element(s) ကို စထည့်မယ့် destination index ပါ။
- Second argument - copy လုပ်မယ့် first element ရဲ့ index ပါ။ Omit လုပ်ရင် `0` ကိုအစားထိုးပါတယ်။ Negative number သုံးလို့ရပါတယ်။
- Third arguemnt - copy ကူးမယ့် အပိုင်းအစ(slice) အဆုံး ရဲ့ index ပါ။ Omit လုပ်ရင် length of the array ကို အစားထိုးပါတယ်။ အဆုံး index က copy ကူးတဲ့ထဲမှာ exclusive ဖြစ်ပါတယ်။ Negative number သုံးလို့ရပါတယ်။

```javascript
        let a = [1,2,3,4,5];
        a.copyWithin(1);        
        
        // destination က index no. 1
        // 2nd argument က 0
        // 3rd argument က end of the array 
        // => returns [1,1,2,3,4]

        a.copyWithin(2,3,5);
        // => returns [1,1,3,4,4]

        a.copyWithin(0, -2)
        // 3rd argument is omitted
        // => returns [4,4,3,4,4]
```

# 4. Array Searching and Sorting Methods[^16]

| indexOf( )<br>lastIndexOf( ) | includes( ) | sort ( ) | reverse( )
| --- | --- | --- | --- |
| search an array | search an array | sort an array | sort an array |
| returns the index | returns true / false | returns a modified array | returns a modified array  |
| do no modify an array | do not modify an array | modify an array | modify an array |
### 4.1 indexOf( ) and lastIndexOf( )
ပေးလိုက်တဲ့ value ကို array ထဲမှာ ရှာပြီး ပထမဆုံးတွေ့တဲ့ element ရဲ့ index ကို return ပြန်ပါတယ်။  မတွေ့ရင် `-1` ပြန်ပါတယ်။  `indexOf()` က beginning to end ရှာပြီး `lastIndexOf()` က end to beginning ရှာပါတယ်။ 

```javascript
        let a = [0,1,2,1,0];
        a.indexOf(1);           // => 1; a[1] is 1
        a.lastIndexOf(1);       // => 3;
        a.indexOf(3);           // => -1;
```
Optional second argument ပေးလို့ရပြီး second argument က စရှာရမယ့် array ရဲ့ index ပါ။  Second argument ကို negative value ပေးရင် array length ကနေ ပြန်နုတ်ပြီး စမှာပါ။   

ဒီ method ၂ ခုက array element တွေကို === နဲ့ compare လုပ်ပြီး array မှာ primitive value တွေအစား object တွေပါလာရင် reference ၂ ခုတူလာကိုပဲ တိုက်စစ်ပေးပါတယ်။[^17]

### 4.2 includes( )
Single argument ကို ယူပြီး အဲ့ဒီ argument က array ထဲမှာပါရင် `ture` ၊ မပါရင် `false` return ပြန်ပါတယ်။  

တိုက်စစ်တဲ့နေရာမှာ `===`ရဲ့ slight variation နဲ့ စစ်တာကြောင့် `indexOf()` မှာ `NaN` ကို `NaN` နဲ့ မတူဘူးလို့ အဖြေထွက်ပေမယ့် `includes()` က တော့ `NaN` က `NaN` နဲ့ <em>တူ</em> တယ်လို့ အဖြေထွက်ပါတယ်။ ဒါကြောင့် `indexOf()` က NaN ကို array ထဲမှာ detect မလုပ်ပေမယ့် `includes()` ကတော့ detect <em>လုပ်</em> ပါတယ်။

```javascript
        let a = [1,true,3,NaN];
        a.includes(true);       // => true
        a.includes(2);          // => false
        a.includes(NaN);        // => true

        a.indexOf(NaN);         // => -1
```
### 4.3 sort( )
Array element တွေကို in place မှာပဲ(လိုအပ်ရင် string အဖြစ် temporarily convert လုပ်ပြီး) alphabetical order နဲ့ sort လုပ်ပေးပါတယ်။ အကယ်လို့ array ကို alphabetical order မဟုတ်ပဲ အခြား order နဲ့ sort လုပ်ချင်ရင် comparison function ကို argument အနေနဲ့ pass လုပ်လို့ရပါတယ်။ 

Comparison function ရဲ့ return value က:
- negative -> 1st argument stays before 2nd argument
- zero     -> remains unchanged
- positive -> 2nd argument moves before 1st argument

```javascript
let a [33, 4, 1111, 222];
a.sort();  // a == [1111, 2222, 33, 4]; alphabetical order
a.sort(function(a,b) {
        return a - b;
});        // a = [4, 33, 222, 1111]; numerical order
```
[^18]

### 4.4 reverse( )
Array element တွေကို reverse order နဲ့ စီပြီး reversed array ကို return ပြန်ပါတယ်။  New array မထုတ်ပဲ in place ပဲ rearrange လုပ်ပြီး reversed array ကို return ပြန်တာပါ။  

[^1]: ဒီ note က ([CSS: The Definitive Guide, 5th Edition by Eric Meyer, Estelle Weyl](https://www.oreilly.com/library/view/css-the-definitive/9781098117603/)) စာအုပ်ကို refer လုပ်ထားတာဖြစ်ပြီး ၊ ကျွန်တော်ပြန်ဖတ်ဖို့ ကျွန်တော့ရဲ့ ကိုယ်ပိုင် study note တစ်ခုသာဖြစ်လို့ အမှားပါကောင်းပါနိုင်ပါတယ်။  
[^2]: page 166
[^3]: page 166
[^4]: page 167
[^5]: page 167
[^6]: page 167
[^7]: ChatGPT
[^8]: page 168
[^9]: page 169
[^10]: ChatGPT
[^11]: ChatGPT
[^12]: page 170
[^13]: page 170
[^14]: Stack: last in first out; Queue: first in first out
[^15]: page 172
[^16]: page 174
[^17]: အသေးစိပ်ကို sn20 မှာဖတ်ပါ။
[^18]: reverse order နဲ့ စီတဲ့နေရာမှာ မြုပ်ကွက်တွေရှိပါတယ်။ sn21 ကိုဖတ်ပါ။
