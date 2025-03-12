[G] Absolutely, let's illustrate how event capturing can be used for debugging, filtering events, and handling mouse drags.

**1. Debugging with Capturing**

* **Scenario:** You have a complex DOM structure and want to see the order in which events are propagating.
* **Implementation:**

    ```html
    <!DOCTYPE html>
    <html>
    <head>
      <title>Capturing Debugging</title>
    </head>
    <body>
      <div id="outer">
        <div id="inner">
          <button id="myButton">Click Me</button>
        </div>
      </div>

      <script>
        document.addEventListener("click", (event) => {
          console.log("Capturing:", event.target.tagName);
        }, true); // Capturing phase
      </script>
    </body>
    </html>
    ```

* **Explanation:**
    * We add a capturing event listener to the `document` object.
    * Whenever a click event occurs anywhere in the document, this listener will be triggered during the capturing phase.
    * The `console.log()` statement will output the tag name of the target element, showing the event's path down the DOM tree.
    * This is very useful to see the order that events occur when they are nested.

**2. Filtering Events with Capturing and Cancellation**

* **Scenario:** You want to prevent certain events from reaching their target elements based on specific conditions.
* **Implementation:**

    ```html
    <!DOCTYPE html>
    <html>
    <head>
      <title>Capturing Filtering</title>
    </head>
    <body>
      <div id="outer">
        <div id="inner">
          <button id="myButton">Click Me (Prevented)</button>
        </div>
      </div>

      <script>
        document.addEventListener("click", (event) => {
          if (event.target.id === "myButton") {
            console.log("Event filtered!");
            event.stopPropagation(); // Prevent further propagation
          }
        }, true); // Capturing phase

        document.getElementById("myButton").addEventListener("click", () => {
          console.log("Button clicked (This will not be shown)!");
        });
      </script>
    </body>
    </html>
    ```

* **Explanation:**
    * We add a capturing event listener to the `document` object.
    * If the target element of the click event is the button with the ID "myButton," we call `event.stopPropagation()`.
    * `event.stopPropagation()` stops the event from propagating further down the DOM tree, preventing the target event listener from being invoked.
    * In this case, the second log message will not be displayed.

**3. Handling Mouse Drags with Capturing**

* **Scenario:** You want to drag an element and ensure that mouse motion events are handled by the dragged element, even when the mouse moves over other elements.
* **Implementation (Simplified):**

    ```html
    <!DOCTYPE html>
    <html>
    <head>
      <title>Capturing Mouse Drag</title>
      <style>
        #draggable {
          width: 100px;
          height: 100px;
          background-color: lightblue;
          position: absolute;
        }
      </style>
    </head>
    <body>
      <div id="draggable"></div>

      <script>
        const draggable = document.getElementById("draggable");
        let isDragging = false;
        let offsetX, offsetY;

        draggable.addEventListener("mousedown", (event) => {
          isDragging = true;
          offsetX = event.clientX - draggable.offsetLeft;
          offsetY = event.clientY - draggable.offsetTop;
        });

        document.addEventListener("mousemove", (event) => {
          if (isDragging) {
            draggable.style.left = event.clientX - offsetX + "px";
            draggable.style.top = event.clientY - offsetY + "px";
          }
        }, true); // Capturing phase

        document.addEventListener("mouseup", () => {
          isDragging = false;
        }, true); // Capturing phase
      </script>
    </body>
    </html>
    ```

* **Explanation:**
    * We add a `mousedown` event listener to the draggable element to start the drag.
    * We add `mousemove` and `mouseup` event listeners to the `document` object with the third argument set to `true` (capturing phase).
    * This ensures that the `mousemove` and `mouseup` events are always captured by the document, regardless of where the mouse is moved.
    * This prevents other elements from interfering with the drag operation.

**Key Takeaways:**

* **Debugging:** Capturing can help visualize event propagation.
* **Filtering:** Capturing and `event.stopPropagation()` can filter events.
* **Mouse Drags:** Capturing ensures consistent event handling during drag operations.
* Capturing is most useful when you want to handle events before they reach the intended target.
