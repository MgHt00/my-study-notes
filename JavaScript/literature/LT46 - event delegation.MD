[G] Yes, this technique is called **event delegation**, and it's a very powerful way to handle events efficiently. Let's illustrate it with an example:

**Scenario:**

Imagine you have a list of items, and you want to handle click events on each item. Instead of attaching a click event listener to each individual item, you can attach a single listener to their common parent element.

**HTML Structure:**

```html
<!DOCTYPE html>
<html>
<head>
  <title>Event Delegation</title>
</head>
<body>
  <ul id="itemList">
    <li class="item" data-item-id="1">Item 1</li>
    <li class="item" data-item-id="2">Item 2</li>
    <li class="item" data-item-id="3">Item 3</li>
    <li class="item" data-item-id="4">Item 4</li>
  </ul>

  <script>
    const itemList = document.getElementById("itemList");

    itemList.addEventListener("click", function(event) {
      // Check if the clicked element is an item
      if (event.target.classList.contains("item")) {
        const itemId = event.target.dataset.itemId;
        console.log("Item clicked:", itemId);
        // Perform actions based on the clicked item
        event.target.style.backgroundColor = "lightgreen";
      }
    });
  </script>
</body>
</html>
```

**Explanation:**

1.  **Single Listener on Parent:**
    * We attach a single click event listener to the `itemList` (the `<ul>` element).

2.  **Event Bubbling:**
    * When you click on an `<li>` element, the click event bubbles up to the `<ul>` element.

3.  **Event Target:**
    * Inside the event handler, `event.target` refers to the element that was actually clicked (the `<li>` element).

4.  **Checking the Target:**
    * We use `event.target.classList.contains("item")` to check if the clicked element has the "item" class.
    * This ensures that we only handle clicks on list items, not other elements within the `<ul>`.

5.  **Accessing Item Data:**
    * We use `event.target.dataset.itemId` to access the `data-item-id` attribute of the clicked item.
    * This allows us to identify which item was clicked.

6.  **Performing Actions:**
    * We can then perform actions based on the clicked item, such as displaying information or modifying the item's appearance.

**Benefits of Event Delegation:**

* **Improved Performance:**
    * Reduces the number of event listeners, which can improve performance, especially when dealing with a large number of elements.

* **Dynamic Elements:**
    * Works with dynamically added elements. If you add new `<li>` elements to the list, you don't need to attach new event listeners to them. The existing listener on the `<ul>` will handle them.

* **Reduced Memory Usage:**
    * Fewer event listeners mean less memory usage.

* **Cleaner Code:**
    * Simplifies event handling logic by centralizing it in a single place.

**When to Use Event Delegation:**

* When you have a large number of similar elements that need to handle the same event.
* When you are dynamically adding or removing elements.

Event delegation is a very useful technique to know.
