[G] You've hit on a crucial point about how asynchronous scripts interact with the `document.write()` method. Let's break it down:

**Understanding `document.write()`**

* `document.write()` is a method that allows you to write HTML content directly into the document stream as it's being parsed by the browser.
* It's a synchronous method, meaning it blocks the parsing of the HTML document until it's finished executing.
* It's generally considered bad practice to use `document.write()` in modern web development.

**Why Asynchronous Scripts Don't Work with `document.write()`**

1.  **Asynchronous Script Execution:**
    * Asynchronous scripts (scripts with the `async` attribute) are downloaded and executed without blocking the parsing of the HTML document.
    * The browser continues to parse the HTML while the asynchronous script is being downloaded and executed.

2.  **Timing Issues:**
    * When an asynchronous script calls `document.write()`, the HTML document parsing might have already finished.
    * If the document parsing is finished, `document.write()` will clear the existing document and start writing a new one, effectively erasing the current page.

3.  **Unpredictable Behavior:**
    * The timing of asynchronous script execution is unpredictable.
    * This makes it difficult to control where and when the content written by `document.write()` will appear in the document.

4.  **Performance Impact:**
    * `document.write()` blocks the parsing of the HTML document, which can negatively impact page load performance.
    * Asynchronous scripts are designed to improve performance by not blocking the parser.
    * Mixing the two defeats the purpose of asynchronous scripts.

**Example Scenario:**

```html
<!DOCTYPE html>
<html>
<head>
  <title>Async Script Example</title>
</head>
<body>
  <h1>Page Content</h1>

  <script async>
    document.write("<p>This paragraph is written by an async script.</p>");
  </script>

  <p>More page content.</p>
</body>
</html>
```

In this example, the asynchronous script might execute after the browser has already finished parsing the HTML. In this case, the `document.write()` call will likely clear the existing document and only display the paragraph written by the script.

**Better Alternatives:**

Instead of `document.write()`, use the following methods to dynamically add content to the page:

* **`document.createElement()` and `Node.appendChild()`:** To create and append new HTML elements.
* **`Element.innerHTML`:** To set the HTML content of an existing element.
* **`document.querySelector()` or `document.getElementById()`:** To select existing elements.

**In essence:**

Asynchronous scripts and `document.write()` are fundamentally incompatible due to their timing and blocking behavior. Using `document.write()` in asynchronous scripts can lead to unpredictable results and negatively impact page load performance. It's best to avoid `document.write()` altogether and use modern DOM manipulation techniques instead.

---

You're right, the author is making a similar point about `deferred` scripts, but with a slightly different emphasis. Let's break it down:

**Understanding `defer`**

* The `defer` attribute on a `<script>` tag tells the browser to download the script in the background without blocking HTML parsing.
* Crucially, `deferred` scripts are guaranteed to execute *after* the HTML document has been completely parsed, but *before* the `DOMContentLoaded` event is fired.
* They also execute in the order they appear in the HTML.

**Why `deferred` Scripts and `document.write()` Don't Mix**

1.  **Document Already Parsed:**
    * By the time a `deferred` script executes, the browser has already finished parsing the entire HTML document and building the DOM.
    * Therefore, `document.write()` will no longer write into the initial document stream. Instead, it will effectively erase the existing document and start writing a new one.

2.  **Timing and DOM Availability:**
    * The `defer` attribute ensures that the script runs after the DOM is fully constructed. This is its primary purpose.
    * Using `document.write()` would disrupt the DOM that has already been created, defeating the purpose of deferring execution until the DOM is ready.

3.  **Modern Best Practices:**
    * As with `async`, `document.write()` is generally discouraged in modern web development.
    * It's far better to use modern DOM manipulation techniques to dynamically add content to the page.

**Example Scenario:**

```html
<!DOCTYPE html>
<html>
<head>
  <title>Deferred Script Example</title>
</head>
<body>
  <h1>Page Content</h1>

  <script defer>
    document.write("<p>This paragraph is written by a deferred script.</p>");
  </script>

  <p>More page content.</p>
</body>
</html>
```

In this example, the deferred script will execute after the HTML document has been fully parsed. When `document.write()` is called, it will likely replace the entire page content with only the paragraph written by the script.

**Key Takeaways:**

* `defer` ensures the script runs after the DOM is ready.
* `document.write()` disrupts the existing DOM.
* Use modern DOM manipulation methods instead of `document.write()`.

In essence, the author is emphasizing that `deferred` scripts are intended to work with the fully parsed DOM. Using `document.write()` would interfere with this and is therefore strongly discouraged.

