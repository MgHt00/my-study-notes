Yes, you can include the calling function's name in the console log to provide more context:

---

### 1. **Pass the Function Name as an Argument**

You can pass the caller's name explicitly as a parameter to `toggleFrameVisibility`:

```javascript
toggleFrameVisibility(mode, target, callerName) {
  console.info(`toggleFrameVisibility() called by ${callerName}: mode: ${mode}`);
  switch (mode) {
    case "show":
      return this.removeClass(target, "hidden");
    case "hide":
      return this.addClass(target, "hidden");
    default:
      console.warn("Invalid mode. Use 'show' or 'hide'.");
      return this;
  }
}

toggleFrameOrderMessage(mode) {
  return this.toggleFrameVisibility(mode, this.frameOrderMessage, "toggleFrameOrderMessage");
}

toggleFrameSKUContainer(mode) {
  return this.toggleFrameVisibility(mode, this.frameSKUContainer, "toggleFrameSKUContainer");
}
```

**Pros**:  
- Simple and easy to understand.

**Cons**:  
- Requires manually specifying the function name, which could lead to mistakes if the function name changes.

---

### 2. **Use `arguments.callee.caller`**

You can dynamically determine the caller using `arguments.callee.caller`. Note that this approach is not recommended for strict mode (`"use strict"`) as `arguments.callee` is deprecated.

```javascript
toggleFrameVisibility(mode, target) {
  const callerName = toggleFrameVisibility.caller?.name || "Unknown";
  console.info(`toggleFrameVisibility() called by ${callerName}: mode: ${mode}`);
  
  switch (mode) {
    case "show":
      return this.removeClass(target, "hidden");
    case "hide":
      return this.addClass(target, "hidden");
    default:
      console.warn("Invalid mode. Use 'show' or 'hide'.");
      return this;
  }
}

toggleFrameOrderMessage(mode) {
  return this.toggleFrameVisibility(mode, this.frameOrderMessage);
}

toggleFrameSKUContainer(mode) {
  return this.toggleFrameVisibility(mode, this.frameSKUContainer);
}
```

**Pros**:  
- Automatically captures the caller's name without hardcoding it.

**Cons**:  
- **Deprecated** in strict mode and modern JavaScript standards.
- May not be reliable in all environments (e.g., minified code, optimizers).

---

### 3. **Use `new Error().stack` for Modern Debugging**

You can use `Error().stack` to get the stack trace and parse the caller's function name dynamically. This works even in strict mode.

```javascript
toggleFrameVisibility(mode, target) {
  const stack = new Error().stack;
  const callerName = stack.split("\n")[2]?.trim().split(" ")[1] || "Unknown";
  console.info(`toggleFrameVisibility() called by ${callerName}: mode: ${mode}`);
  
  switch (mode) {
    case "show":
      return this.removeClass(target, "hidden");
    case "hide":
      return this.addClass(target, "hidden");
    default:
      console.warn("Invalid mode. Use 'show' or 'hide'.");
      return this;
  }
}

toggleFrameOrderMessage(mode) {
  return this.toggleFrameVisibility(mode, this.frameOrderMessage);
}

toggleFrameSKUContainer(mode) {
  return this.toggleFrameVisibility(mode, this.frameSKUContainer);
}
```

**Pros**:  
- Works in modern JavaScript, including strict mode.
- No need to manually pass function names.

**Cons**:  
- Parsing stack traces can be less efficient.
- Stack trace formats may vary between browsers.

---

### Recommendation

- **For simplicity** and **reliability**, **passing the function name explicitly** (method 1) is the best option.
- If you need a more dynamic approach, **parsing the stack trace** (method 3) is modern and works across environments.

I hope this helps! Let me know which approach you prefer. 😊
