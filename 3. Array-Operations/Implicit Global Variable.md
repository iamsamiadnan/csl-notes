If you don't use `const`, `let`, or `var` when declaring `attendeeName` inside the `for...of` loop, JavaScript will treat `attendeeName` as an **implicitly global variable**. Here's what happens in that scenario:

- **Implicit Global Variable**: When you omit a keyword (like `const`, `let`, or `var`), JavaScript looks for a variable named `attendeeName` in the current scope. If it doesn't find one, it creates a new global variable named `attendeeName` and assigns the value to it.
    
- **Global Scope Issue**: This means that the variable `attendeeName` would exist globally and could be modified or accessed outside of the loop. This behavior is generally considered bad practice because it can lead to unexpected side effects or bugs, especially if other parts of the code also use `attendeeName`.

```js
for (attendeeName of attendeeNames) {
  // Now attendeeName is implicitly global.
  console.log(attendeeName);
}

console.log(attendeeName); // The last value of attendeeName from the loop is accessible here.

```