[G] You're asking about the viewport-percentage length units in CSS, including the newer ones designed to address inconsistencies with dynamic toolbars on mobile devices. Let's break them down:

**Basic Viewport Units:**

* **`vw` (viewport width):** 1vw is equal to 1% of the width of the initial containing block (the viewport).
* **`vh` (viewport height):** 1vh is equal to 1% of the height of the initial containing block (the viewport).

    These units are relative to the dimensions of the browser window. However, on mobile devices, the height of the viewport can be affected by the appearance and disappearance of the address bar and other browser UI elements, leading to the "100vh problem" where an element styled with `height: 100vh` might be taller than the visible screen.

**Newer Viewport Units (Addressing Dynamic Toolbars):**

To address the issues with `vh` on mobile, newer viewport units have been introduced in the CSS Viewport Module Level 1 specification:

* **`lvw` (large viewport width):** Represents 1% of the large viewport's width. The large viewport is defined as the viewport sized assuming any UA interfaces that are transient but normally present are fully expanded. This is typically the width of the browser window when all toolbars are visible.

* **`lvh` (large viewport height):** Represents 1% of the large viewport's height. Similar to `lvw`, this is the height of the viewport when all dynamic toolbars are assumed to be fully expanded (visible).

* **`svw` (small viewport width):** Represents 1% of the small viewport's width. The small viewport is sized assuming any UA interfaces that are transient but normally present are fully contracted. This is typically the width of the browser window when all such toolbars are fully hidden.

* **`svh` (small viewport height):** Represents 1% of the small viewport's height. This is the height of the viewport when all dynamic toolbars are assumed to be fully contracted (hidden), maximizing the available screen space.

* **`dvw` (dynamic viewport width):** Represents 1% of the dynamic viewport's width. The dynamic viewport is sized to the current state of any UA interfaces. This means its width might change if, for example, a sidebar is toggled.

* **`dvh` (dynamic viewport height):** Represents 1% of the dynamic viewport's height. This unit is crucial for addressing the mobile toolbar issue. The `dvh` unit reflects the currently visible height of the viewport, so an element with `height: 100dvh` will always fit the visible screen, even as toolbars appear and disappear.

**In Summary:**

* `vw` and `vh` are the traditional viewport units, relative to the initial viewport size. They can have inconsistencies on mobile due to dynamic toolbars.

* `lvw` and `lvh` represent the viewport dimensions assuming all dynamic toolbars are visible (the "largest" possible viewport).

* `svw` and `svh` represent the viewport dimensions assuming all dynamic toolbars are hidden (the "smallest" possible viewport).

* `dvw` and `dvh` represent the **actual, currently visible** viewport dimensions, dynamically adjusting as toolbars appear or disappear. These are the most reliable units for achieving true full-viewport height on mobile.

**When to Use Which:**

* For basic responsive layouts where dynamic toolbars aren't a major concern (e.g., desktop-focused sites), `vw` and `vh` might suffice.

* When dealing with mobile layouts where you need an element to always fill the visible screen height without being cut off by toolbars, `dvh` is the recommended unit. Similarly, `dvw` can be used for full-width elements that need to adapt to dynamic width changes.

* `lvh`/`lvw` and `svh`/`svw` can be useful in specific scenarios where you want to consider the extremes of the viewport size with toolbars fully visible or hidden, perhaps for more intricate layout adjustments or animations that respond to these state changes.

**Browser Support:**

Support for the dynamic viewport units (`dvw`, `dvh`, `svw`, `svh`, `lvw`, `lvh`) has been increasing in modern browsers, but it's still not universally supported. It's advisable to check the current browser compatibility on resources like "Can I Use..." and potentially provide fallbacks using `vh` for older browsers.

Understanding these viewport units allows for more precise and reliable responsive design, especially when targeting mobile devices with their dynamic user interfaces.
