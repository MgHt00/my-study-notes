# To fetch a value from a CSS variable in JavaScript [^1]

    // Fetching the value of the --no-of-sqs CSS variable
    const rootStyles = getComputedStyle(document.documentElement);
    const noOfSqs = parseInt(rootStyles.getPropertyValue('--no-of-sqs'));
    
    const squareFrame = document.querySelector("#square-frame");
    
    function generateSqs(sqs) {
      for (let r = 0; r < sqs; r++) {
        for (let c = 0; c < sqs; c++) {
          const square = document.createElement("div");
          square.className = `sq-${r}-${c}`;
          square.textContent = `${r},${c}`; // Optional: Display the row and column on the square
          squareFrame.appendChild(square);
        }
      }
    }
    
    generateSqs(noOfSqs);

## Explanation:
- Fetching the CSS Variable: `getComputedStyle(document.documentElement).getPropertyValue('--no-of-sqs')` retrieves the value of `--no-of-sqs` from the `:root` selector.
- Conversion: Since CSS variables are strings by default, we use `parseInt` to convert the value to a number.
- Usage in Function: The value of `noOfSqs` is then passed to the `generateSqs` function to create the grid of squares.

This allows your JavaScript to dynamically adjust based on the value set in your CSS.

[^1]: Word Search project မှာ သုံးထားပါတယ်။
