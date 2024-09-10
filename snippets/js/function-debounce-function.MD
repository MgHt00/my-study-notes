The `debounce` function is a common technique used to limit how often a function is executed. It is particularly useful for handling events like scrolling, resizing, or typing, where the associated function might be called frequently and could lead to performance issues. [^1]

Here’s a breakdown of how the `debounce` function works:

### 1. **Function Definition**

```javascript
function debounce(func, delay) {
  let timeoutId;
  return function(event, ...args) {
    clearTimeout(timeoutId);
    timeoutId = setTimeout(() => {
      func.apply(this, [event, ...args]);
    }, delay);
  };
}
```

### 2. **Parameters**

- `func`: The function you want to debounce. This is the function that will be called after the delay.
- `delay`: The time (in milliseconds) to wait before calling `func`.

### 3. **How It Works**

#### 3.1. **Variable to Track Timeout**

```javascript
let timeoutId;
```

- `timeoutId` is used to keep track of the timer. It will be set whenever the debounced function is called and cleared if the function is called again before the timer expires.

#### 3.2. **Return a New Function**

```javascript
return function(event, ...args) {
```

- This returned function is the debounced version of `func`. It is the function that gets called instead of `func` directly.

#### 3.3. **Clear Existing Timeout**

```javascript
clearTimeout(timeoutId);
```

- `clearTimeout(timeoutId)` cancels any previously scheduled invocation of `func`. This means if the debounced function is called multiple times before the delay expires, the previous calls will be ignored.

#### 3.4. **Set a New Timeout**

```javascript
timeoutId = setTimeout(() => {
  func.apply(this, [event, ...args]);
}, delay);
```

- `setTimeout` schedules the execution of `func` after the specified `delay`. 
- `func.apply(this, [event, ...args])` is used to call `func` with the correct `this` context and pass along any arguments.

### 4. **Why It Works**

- **Throttle Function Calls**: The debounced function will only execute `func` once the specified `delay` has passed without any new calls. If the function is called again within the delay period, the previous timer is cleared, and a new timer is set.
- **Performance Improvement**: This technique prevents excessive function calls, which can improve performance and user experience by reducing the number of operations performed in a short period.

### Example Usage

Let’s see a practical example of using `debounce` with a search input:

```javascript
function search(query) {
  console.log("Searching for:", query);
}

const debouncedSearch = debounce(search, 300);

document.querySelector("#search-input").addEventListener('input', (event) => {
  debouncedSearch(event.target.value);
});
```

- **Before Debounce**: If you type quickly into the input field, the `search` function would be called for every keystroke.
- **With Debounce**: The `search` function is only called 300 milliseconds after the last keystroke, reducing the number of search operations.

I hope this helps clarify how `debounce` works! If you have more questions or need further examples, feel free to ask.

[^1]: ChatGPT သင်ပေးထားတာဖြစ်ပြီး ၊ JLPT project ရဲ့ load.js မှာ သုံးထားပါတယ်။  10 Sep 24 နေ့ knowledge နဲ့ ဒီ debounce ကို နားမလည်သေးပါဘူး။ တစ်နေ့တစ်ချိန်ကျ ရှင်းရှင်းလင်းလင်း သိလာမယ် မျှော်လင့်ပါတယ်။  ~မောင်ထူး