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
- iterable object တွေဖြစ်တဲ့ arrays, strings, sets, maps တွေနဲ့ သုံးလို့ရပါတယ်။
- array က iterated live လုပ်ပါတယ်။  ဒါကြောင့် loop ထဲမှာ array ကို push လုပ်တဲ့ expression မျိုးပါနေရင် infinite loop ထွက်နိုင်ပါတယ်။  

#### for/of with objects
- object တွေက (by default) not iterable ပါ။  `for/of` ကို regular object မှာ သုံးရင် `TypeError`ထွက်ပါတယ်။
- `objects.keys()`, `objects.values()`, `objects.entries()` နဲ့သုံးလို့ရပါတယ်။
  - ဒီ methods တွေက property name, value, pair ကို array အနေနဲ့ return ပြန်တာကြောင့် `for/off` နဲ့ သုံးလို့ရသွားတာဖြစ်ပါတယ်။
  - ထုတ်ပြီးသား array ကို `for/of` နဲ့ ပြန် loop တာဖြစ်တာကြောင့် pure array ကို loop သလို object ကို live iterate လုပ်လို့ မရပါဘူး

[^1]: JavaScript The Definitive Guide by David Flanagan - 5.4.1 (p. 105)
[^2]: 5.4.2 (p. 106)
[^3]: 5.4.3 (p. 106)
[^4]: 5.4.4 (p. 108)
