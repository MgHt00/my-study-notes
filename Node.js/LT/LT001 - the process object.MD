The **`process` object** is a global object in Node.js that provides information about, and control over, the currently executing Node.js process. Because it's a global object, you can use it anywhere in your code without needing to use `require()`.

It is one of the most fundamental built-in objects, offering essential utilities for interacting with the operating system (OS) and the running program.

-----

## Key Properties and Methods

Here are some of the most frequently used parts of the `process` object:

### 1\. Interacting with the OS

  * **`process.env`**: An object containing all the **environment variables** of the user environment. This is where Node.js looks for variables like `PATH` and, more importantly, where you access custom variables set via `.env` files (e.g., `process.env.API_KEY`).
  * **`process.argv`**: An array containing the **command-line arguments** passed when the Node.js process was launched.
      * `process.argv[0]` is the path to the `node` executable.
      * `process.argv[1]` is the path to the script file being executed.
      * `process.argv[2]` and beyond are the actual arguments you pass.
  * **`process.cwd()`**: A function that returns the **current working directory** of the Node.js process.

### 2\. Standard Streams (I/O)

These are used for input and output, just like in a traditional command-line program:

  * **`process.stdin`**: A stream for standard **input** (used to read data from the command line).
  * **`process.stdout`**: A stream for standard **output** (used for printing non-error messages, like `console.log`).
  * **`process.stderr`**: A stream for standard **error** (used for printing error messages).

### 3\. Controlling the Process

  * **`process.exit(code)`**: Immediately terminates the Node.js process. The optional `code` is an integer:
      * **`0`**: Indicates a successful termination.
      * **Any non-zero code** (e.g., `1`): Indicates an error or failure.
  * **`process.pid`**: A number that represents the **Process ID** of the current running process, useful for logging or managing multiple processes.

### 4\. Events

The `process` object is also an **EventEmitter**, allowing you to listen for critical events:

  * **`process.on('uncaughtException', (err) => {})`**: Fires when an exception bubbles all the way back to the event loop without being caught in a `try...catch` block. This is a critical last-resort error handler.
  * **`process.on('exit', (code) => {})`**: Fires right before the Node.js process is about to exit. This is a good place to perform final synchronous cleanup operations, though it cannot stop the exit.

-----

## Example Usage

Here's how you might use `process` to read command-line arguments and check the environment:

```javascript
// Example: check arguments and environment
const args = process.argv.slice(2);
const environment = process.env.NODE_ENV;

if (environment === 'production') {
  console.log('Running in production mode.');
} else {
  console.log(`Running in ${environment || 'development'} mode.`);
}

if (args.length > 0) {
  console.log(`Arguments passed: ${args.join(', ')}`);
} else {
  console.log('No arguments passed.');
}

// To run this:
// node your_script.js hello world
```

[G]
