The behavior of `Math.max()` and `Math.min()` in JavaScript when called without any arguments is related to how they are defined:

1. **`Math.max()`**:
   - It returns the *largest* value among the given arguments.
   - When no arguments are provided, it returns `-Infinity` because `-Infinity` is the lowest possible value, and any number will be greater than `-Infinity`.
   - In other words, if you imagine comparing against nothing, `-Infinity` serves as the "smallest" baseline.

   ```javascript
   console.log(Math.max()); // Output: -Infinity
   ```

2. **`Math.min()`**:
   - It returns the *smallest* value among the given arguments.
   - When no arguments are provided, it returns `Infinity` because `Infinity` is the highest possible value, and any number will be smaller than `Infinity`.
   - This means that if you have no values to compare, `Infinity` serves as the "largest" baseline.

   ```javascript
   console.log(Math.min()); // Output: Infinity
   ```

In summary, this behavior ensures that `Math.max()` and `Math.min()` return values that won't accidentally interfere with comparisons when no valid arguments are provided.