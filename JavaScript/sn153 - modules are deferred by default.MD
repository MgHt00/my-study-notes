[G] No, `<script type="module">` is **not** async by default. However, it does have some unique loading behaviors that are important to understand.

Here's a breakdown:

**`<script type="module">` Loading Behavior:**

* **Deferred Execution (by default):**
    * Modules are deferred by default. This means they are downloaded in the background without blocking HTML parsing, and they are executed *after* the HTML document has been fully parsed.
    * This is similar to the `defer` attribute on regular scripts.
* **Ordered Execution:**
    * Modules are executed in the order they appear in the HTML document.
    * This ensures that dependencies between modules are resolved correctly.
* **Asynchronous Downloading:**
    * While the execution is deferred and ordered, the downloading of modules happens asynchronously, in the background.

**Key Differences from `async`:**

* **Execution Timing:**
    * `async` scripts execute as soon as they are downloaded, regardless of the DOM state or other scripts.
    * `<script type="module">` scripts execute after the DOM is fully parsed and in the order they appear.
* **Dependency Resolution:**
    * `async` scripts do not guarantee any specific execution order, making it difficult to manage dependencies.
    * `<script type="module">` scripts maintain the order, which is essential for modules that depend on each other.

**How to Make Modules `async`:**

* You can explicitly add the `async` attribute to `<script type="module">` if you want the module to execute as soon as it's downloaded, regardless of the DOM state. However, be aware that this can cause issues with module dependencies.

**In summary:**

* `<script type="module">` scripts are deferred by default, not async.
* They are downloaded asynchronously but executed in order after the DOM is ready.
* You can add the `async` attribute, but it's generally not recommended unless you understand the implications for module dependencies.
