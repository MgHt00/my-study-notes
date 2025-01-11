When the authors say that `setTimeout()` does not wait for the time to elapse before returning, they mean that the function call itself is asynchronous. This means that when you call `setTimeout()`, it immediately returns control to the next line of code without pausing the execution of the script to wait for the specified delay.

Here's an example to illustrate:

```javascript
console.log("Start");

setTimeout(() => {
  console.log("This runs after 2 seconds");
}, 2000);

console.log("End");
```

In this example:

1. `"Start"` is printed to the console.
2. `setTimeout()` is called with a delay of 2000 milliseconds (2 seconds). However, it does not block the execution and immediately returns, allowing the script to continue.
3. `"End"` is printed to the console right after `"Start"`.
4. After 2 seconds, the callback function inside `setTimeout()` is executed, printing `"This runs after 2 seconds"`.

The key point is that `setTimeout()` schedules the callback to be executed after the delay, but it does not block the script from continuing to run the subsequent code.
