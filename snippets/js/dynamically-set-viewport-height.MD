# Dynamically Set Viewport Height

#### Javascript
    function setVhProperty() {
      let vh = window.innerHeight * 0.01;
      document.documentElement.style.setProperty('--vh', `${vh}px`);
    }

    setVhProperty();

    window.addEventListener('resize', setVhProperty);

Calculate the viewport height (window.innerHeight) and multiply it by 0.01 to get the value for 1vh.

#### CSS
    body {
      height: calc(var(--vh, 1vh) * 100); /* Use the custom property for full viewport height */
    }