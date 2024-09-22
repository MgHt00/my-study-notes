Yes, you can group console messages using `console.group()`, `console.groupCollapsed()`, and `console.groupEnd()`. This helps organize your logs, making it easier to manage and view related messages together.

Here’s how you can use them:

1. **`console.group(label)`**: Starts a new group with an optional label. All subsequent log messages will be indented under this group until you call `console.groupEnd()`.

2. **`console.groupCollapsed(label)`**: Starts a new group that is collapsed by default, allowing you to expand it only when you want to see the logs inside.

3. **`console.groupEnd()`**: Ends the current group.

### Example:
```javascript
console.group("User Data");
// Log some user information
console.log("Name: John Doe");
console.log("Age: 30");
console.group("Address");
console.log("City: New York");
console.log("State: NY");
console.groupEnd();
console.groupEnd();
```

In this example, the user data will be grouped together, and the address will be nested within it. You can expand or collapse the groups in the console to make it easier to navigate through your logs. This is especially useful for organizing output in larger applications or during debugging sessions.
