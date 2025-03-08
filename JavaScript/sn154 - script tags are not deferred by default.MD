[G] No, ordinary `<script>` tags are **not** deferred by default. This is a very common point of confusion, so it's good to clarify.

Here's the breakdown of how ordinary `<script>` tags behave:

**Ordinary `<script>` Tags (Without `async` or `defer`)**

* **Blocking Behavior:**
    * When the browser encounters an ordinary `<script>` tag, it immediately stops parsing the HTML document.
    * It then downloads and executes the script.
    * Only after the script has finished executing does the browser resume parsing the rest of the HTML.
* **Synchronous Execution:**
    * Scripts are executed in the order they appear in the HTML document.
    * This means that if a script takes a long time to download or execute, it will block the rendering of the page.
* **No Deferred Execution:**
    * Ordinary `<script>` tags do not wait for the DOM to be parsed before executing.

**Why This Matters**

* **Page Load Performance:** Blocking behavior can significantly impact page load performance, as the browser cannot render the rest of the page until the script has finished.
* **DOM Manipulation:** If a script tries to manipulate the DOM before it's fully loaded, it might encounter errors or unexpected behavior.

**How to Change the Behavior**

* **`async`:** To download the script asynchronously without blocking parsing and execute it as soon as it's available.
* **`defer`:** To download the script asynchronously without blocking parsing and execute it after the DOM is fully parsed, in the order they appear.
* **`<script type="module">`:** To treat the script as a module, which has deferred execution by default.

**In summary:**

* Ordinary `<script>` tags block HTML parsing and execute immediately.
* They are not deferred by default.
* Use `async` or `defer` to change the loading behavior and improve performance.
