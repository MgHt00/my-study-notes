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
- the `do` loop must always be terminited with a semicolon.
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

[^1]: JavaScript The Definitive Guide by David Flanagan - 5.4.1 (p. 105)
[^2]: 5.4.2 (p. 106)
[^3]: 5.4.3 (p. 106)
