The `console.time()`, `console.timeLog()`, and `console.timeEnd()` methods are used for timing code execution, which can help measure the performance of different parts of your code.

### Example 1: Basic Timing

```javascript
console.time("myTimer");

for (let i = 0; i < 1000000; i++) {
  // Simulate some code that takes time
}

console.timeEnd("myTimer");
```

In this example:
- `console.time("myTimer")` starts the timer with the label "myTimer."
- After running a loop, `console.timeEnd("myTimer")` stops the timer and logs the elapsed time with the label "myTimer."

### Example 2: Using `console.timeLog()`

```javascript
console.time("processTimer");

for (let i = 0; i < 1000000; i++) {
  // Simulate some code that takes time
  if (i === 500000) {
    console.timeLog("processTimer", "Halfway through the loop");
  }
}

console.timeEnd("processTimer");
```

In this example:
- `console.time("processTimer")` starts the timer.
- `console.timeLog("processTimer", "Halfway through the loop")` logs the elapsed time at the halfway point of the loop without stopping the timer.
- `console.timeEnd("processTimer")` stops the timer at the end of the loop and logs the total time.

### Example 3: Multiple Timers

```javascript
console.time("timer1");

setTimeout(() => {
  console.timeEnd("timer1");
}, 1000);

console.time("timer2");

setTimeout(() => {
  console.timeEnd("timer2");
}, 2000);
```

In this example:
- Two timers, "timer1" and "timer2," are started with `console.time()`.
- `console.timeEnd()` is used to stop each timer after different delays, showing how you can manage multiple timers simultaneously.

These methods provide a simple way to benchmark and optimize your code by giving insights into how long specific sections take to execute.
