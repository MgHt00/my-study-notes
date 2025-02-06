[G] You're absolutely correct! 

* **If `p1` is a Promise that is already in the process of rejecting:**
    * Calling `Promise.resolve()` on `p1` **will not change its state**. 
    * `p1` will still **reject** with the original error.

* **The Promise returned by `Promise.resolve(p1)`:**
    * This new Promise will **simply mirror the state of `p1`**. 
    * Since `p1` is rejecting, the new Promise will also **reject** with the same error.

**Key takeaway:**

`Promise.resolve()` doesn't have the power to "override" or "rescue" a Promise that's already in the process of rejection. It essentially "observes" the state of the input Promise and reflects that state in its own resolution or rejection.

I hope this further clarifies the interaction between `Promise.resolve()` and a rejecting Promise!
