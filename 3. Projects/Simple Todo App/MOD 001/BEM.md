BEM, short for **Block Element Modifier**, is a popular naming convention in CSS used to make code more readable and modular. Here’s how it works:

### 1. **Block**
   - The **Block** represents a standalone component that can exist independently. It’s the main “container” of your UI component.
   - **Example**: `.button`, `.card`, `.header`

### 2. **Element**
   - An **Element** is a part of a block and has no standalone meaning. It’s tied to the block and is usually a child component.
   - Elements are written as `block__element`, with two underscores connecting the block and element names.
   - **Example**: `.button__icon`, `.card__title`, `.header__nav`

### 3. **Modifier**
   - A **Modifier** represents a different state or variation of a block or element. It changes the appearance or behavior of a block or element without creating a separate component.
   - Modifiers are written as `block--modifier` or `block__element--modifier`, with two dashes.
   - **Example**: `.button--primary`, `.card__title--highlighted`, `.header--fixed`

### Putting It All Together
Imagine you’re styling a card component. Here’s how you might structure it using BEM:

```html
<div class="card card--featured">
    <h2 class="card__title card__title--large">Welcome</h2>
    <p class="card__description">This is a card description.</p>
    <button class="card__button card__button--primary">Click Me</button>
</div>
```

#### CSS Example

```css
/* Block */
.card {
    padding: 20px;
    border: 1px solid #ddd;
}

/* Element */
.card__title {
    font-size: 24px;
    font-weight: bold;
}

.card__description {
    font-size: 16px;
    color: #666;
}

/* Modifier */
.card--featured {
    border-color: gold;
}

.card__title--large {
    font-size: 32px;
}

.card__button--primary {
    background-color: blue;
    color: white;
}
```

### Key Benefits of BEM
- **Clarity**: BEM names are descriptive and help you understand the structure and hierarchy.
- **Reusability**: BEM allows you to reuse blocks with different elements or modifiers.
- **Predictability**: BEM’s structure makes it easy to locate styles and understand relationships. 

BEM encourages consistency and scalability, making it especially useful in larger projects with complex components.