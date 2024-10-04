# while[^1]
```javascript
while (expression)
  statement
```
The interpreter executes `statement` repeatedly `shile the `expression` is truthy

# do/while[^2]
```javascript
do
  statement
while (expression);
```
- the `do` loop must always be terminated with a semicolon.
- the loop expression is tested at the bottom of the loop
- the body of the loop is always executed at least once.

# for[^3]
```javascript
for(initialize ; test ; increment)
  statement
```
- the equivalent `while` loop would be:
```javascript
initialize;
while(test) {
  statement
  increment;
{
```
`for` loop provides a way to combine multiple initialization and increment expressions into a single expression:
```javascript
let i, j, sum = 0;
for(i = 0, j = 10 ; i < 10 ; i++, j--) {
  sum += i * j;
}
```

# for/of[^4]
```javascript
for(let element of data){

}
```
- iterable object တွေဖြစ်တဲ့ arrays, strings, sets, maps တွေနဲ့ သုံးလို့ရပါတယ်။
- array က iterated live လုပ်ပါတယ်။  ဒါကြောင့် loop ထဲမှာ array ကို push လုပ်တဲ့ expression မျိုးပါနေရင် infinite loop ဖြစ်သွားနိုင်ပါတယ်။  
- loop body ကို execute မလုပ်ခင်တိုင်း array ရဲ့ next element ကို `element` variable ထဲ assign လုပ်ပါတယ်။

#### for/of with objects
- object တွေက (by default) not iterable ပါ။  `for/of` ကို regular object မှာ သုံးရင် `TypeError`ထွက်ပါတယ်။
- `Object.keys()`, `Object.values()`, `Object.entries()` နဲ့သုံးလို့ရပါတယ်။
  - ဒီ methods တွေက property name, value, pair ကို array အနေနဲ့ return ပြန်တာကြောင့် `for/off` နဲ့ သုံးလို့ရသွားတာဖြစ်ပါတယ်။
  - ထုတ်ပြီးသား array ကို `for/of` နဲ့ ပြန် loop တာဖြစ်တာကြောင့် pure array ကို loop သလို object ကို live iterate လုပ်လို့ မရပါဘူး
```javascript
for(let element of o) {
  // Throws TypeError
}

for(let k of Object.keys(o)) {
  // Object.keys() -> [ , , ]
}

for(let v of Object.values(o)) {
  // Object.values() -> [ , , ]
}

for(let [k,v] of Object.entries(o)) {
  // Object.entries() -> [ [ , ], [ , ], [ , ]]
}
```

# for/in[^5]
- any object ကို loop လို့ရပါတယ်။
- အဓိက point က specified လုပ်ထားတဲ့ object ရဲ့ **property name** ကို loop ပါတယ်။ 
```javascript
for (variable in object)
  statement
```
- `object` expression ကို အရင် evaluate လုပ်ပြီး`null / undefined` ဆိုရင် loop ကို ကျော်ပါတယ်။ 
- iteration တစ်ခု မလုပ်ခင်တိုင်း JavaScript intepreter က `variable` expression ကို evaluate လုပ်ပြီး name of the property (a string value) ကို `variable` ထဲ assign လုပ်ပါတယ်။ 

JavaScript array တွေက special kind of object ဖြစ်တာကြောင့် array ကို `for/in` နဲ့ loop ရင် array ရဲ့ property name ဖြစ်တဲ့ index ကို ထုတ်ပေးပါတယ်။ 

[^1]: JavaScript The Definitive Guide by David Flanagan - 5.4.1 (p. 105)
[^2]: 5.4.2 (p. 106)
[^3]: 5.4.3 (p. 106)
[^4]: 5.4.4 (p. 108)
[^5]: 5.4.5 (p. 111)
