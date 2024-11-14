No, `:root` is not mandatory to declare CSS variables, but it is commonly used because it represents the highest-level scope in the document. Declaring variables in `:root` makes them available globally, meaning you can access them anywhere in your CSS.

However, you can define CSS variables within any selector or scope. If you declare them in a specific class or element, their scope will be limited to that selector and any descendants.

### Examples

1. **Using `:root` for global scope (recommended for global variables):**

   ```css
   :root {
     --primary-color: #3498db;
   }

   button {
     background-color: var(--primary-color);
   }
   ```

2. **Declaring a variable in a specific class (local scope):**

   ```css
   .card {
     --card-background: #f5f5f5;
     background-color: var(--card-background);
   }
   ```

   Here, `--card-background` is only available within the `.card` class or its descendants.

3. **Defining variables inline on elements (inline scope):**

   ```html
   <div style="--dynamic-color: coral;">
     <p style="color: var(--dynamic-color);">This is coral colored.</p>
   </div>
   ```

In summary, `:root` is not mandatory, but it’s useful when you want your variables to be globally accessible across your CSS.