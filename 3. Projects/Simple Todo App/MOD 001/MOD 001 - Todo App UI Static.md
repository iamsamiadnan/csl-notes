
todo-app/
├── index.html
├── assets/
│   ├── css/
│   │   └── style.css
│   ├── js/
│   │   └── app.js
│   └── images/ (optional, if you have images)
└── README.md (optional, for documentation)

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple Todo App</title>
    <link rel="stylesheet" href="assets/css/style.css">
</head>
<body>
    <div class="card">
        <ul class="card__list">
            <li class="card__list-item">Task 1 <button class="button button--primary" type="button">Delete</button></li>
            <li class="card__list-item">Task 1 <button class="button button--primary" type="button">Delete</button></li>
            <li class="card__list-item">Task 1 <button class="button button--primary" type="button">Delete</button></li>
        </ul>
        <input class="card__input" type="text"> <button class="button button--danger" type="text">Add</button>
    </div>

</body>
</html>
```

```css
.card
.card__list
.card__list-item

.button
.button--primary
.button--danger

.card__input
```

[[Box Sizing Border Box]]

Updated HTML
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple Todo App</title>
    <link rel="stylesheet" href="assets/css/style.css">
</head>
<body>
    <div class="card">
        <ul class="card__list">
            <li class="card__list-item">
                Task 1 
                <button class="button button--danger" type="button">
                    <svg height="16px" width="16px" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor"><path d="M17 6H22V8H20V21C20 21.5523 19.5523 22 19 22H5C4.44772 22 4 21.5523 4 21V8H2V6H7V3C7 2.44772 7.44772 2 8 2H16C16.5523 2 17 2.44772 17 3V6ZM18 8H6V20H18V8ZM9 11H11V17H9V11ZM13 11H15V17H13V11ZM9 4V6H15V4H9Z"></path></svg>
                </button>
            </li>
 
        </ul>
        <div class="card__footer">
            <input class="card__input" type="text"> 
            <button class="button button--primary" type="text">
                <svg height="16px" width="16px" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor"><path d="M4 3H20C20.5523 3 21 3.44772 21 4V20C21 20.5523 20.5523 21 20 21H4C3.44772 21 3 20.5523 3 20V4C3 3.44772 3.44772 3 4 3ZM5 5V19H19V5H5ZM11 11V7H13V11H17V13H13V17H11V13H7V11H11Z"></path></svg>
            </button>
        </div>
    </div>

</body>
</html>
```

```css
:root {
    --primary-color: #845ec2;
    --secondary-color: #d65db1;
    --background-color: #fef7ff;
    --text-color: #4b4453;
    --border-color: #d6e5eb;

    --font-family: 'Segoe UI', Arial, sans-serif;
    --button-text-color: #fff;
    --button-danger: #ff8066;
}

body {
    margin: 16px;
    font-family: var(--font-family);
}

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

.card {
    border: 1px solid var(--border-color);
    border-radius: 4px;
    width: max-content;
    padding: 16px;
}

.card__list {
    list-style: none;
    margin-bottom: 16px;
}

.card__list-item {
    margin-bottom: 8px;
    border: 1px solid var(--border-color);
    padding: 4px;
    border-radius: 2px;
    display: flex;
    justify-content: space-between;
}

.card__footer {
    display: flex;
    gap: 2px;
}

.button {
    border: 0;
    line-height: 0;
    cursor: pointer;
    padding: 0 4px;
    border-radius: 2px;
    color: var(--button-text-color);
}

.button:hover {
    opacity: 0.7;
}

.button--primary {
    background-color: var(--primary-color);
}
.button--danger {
    background-color: var(--button-danger);
}
```

## Add Task: Console Log

```html
<script type="module" src="assets/js/app.js"></script>
```

```js
// app.js
import { $ } from "./utils.js";

const tasks = [];

function addTask() {
    const taskText = $('#card__input').value;
    const task = {
        id: tasks.length + 1,
        taskText
    }

    tasks.push(task);

    console.log(tasks);
}

$('#button-add').addEventListener('click', addTask);
```

```js
// utils.js

export function $(id) {
    return document.querySelector(id);
}
```

## Add Task: Update UI

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple Todo App</title>
    <link rel="stylesheet" href="assets/css/style.css">
</head>
<body>
    <div class="card">
        <ul id="card__list" class="card__list">
            <li class="card__list-item">
                Task 1 
                <button class="button button--danger" type="button">
                    <svg height="16px" width="16px" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor"><path d="M17 6H22V8H20V21C20 21.5523 19.5523 22 19 22H5C4.44772 22 4 21.5523 4 21V8H2V6H7V3C7 2.44772 7.44772 2 8 2H16C16.5523 2 17 2.44772 17 3V6ZM18 8H6V20H18V8ZM9 11H11V17H9V11ZM13 11H15V17H13V11ZM9 4V6H15V4H9Z"></path></svg>
                </button>
            </li>
 
        </ul>
        <div class="card__footer">
            <input id="card__input" class="card__input" type="text"> 
            <button id="button-add" class="button button--primary" type="text">
                <svg height="16px" width="16px" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor"><path d="M4 3H20C20.5523 3 21 3.44772 21 4V20C21 20.5523 20.5523 21 20 21H4C3.44772 21 3 20.5523 3 20V4C3 3.44772 3.44772 3 4 3ZM5 5V19H19V5H5ZM11 11V7H13V11H17V13H13V17H11V13H7V11H11Z"></path></svg>
            </button>
        </div>
    </div>

    <script type="module" src="assets/js/app.js"></script>
</body>
</html>
```

```js
// storage.js
export const tasks = [];
```

```js
// app.js
import { tasks } from "./storage.js";
import { $, updateUI } from "./utils.js";



function addTask() {
    const taskText = $('#card__input').value;
    const task = {
        id: tasks.length + 1,
        taskText
    }

    tasks.push(task);

    console.log(tasks);
    updateUI();
}

$('#button-add').addEventListener('click', addTask);
```

```js
import { tasks } from "./storage.js";

export function $(id) {
    return document.querySelector(id);
}

export function updateUI() {
    let cardListItems = '';

    for(const task of tasks) {
        const cardListItem = `
            <li class="card__list-item">
                ${task.taskText}
                <button class="button button--danger" type="button">
                    <svg height="16px" width="16px" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor"><path d="M17 6H22V8H20V21C20 21.5523 19.5523 22 19 22H5C4.44772 22 4 21.5523 4 21V8H2V6H7V3C7 2.44772 7.44772 2 8 2H16C16.5523 2 17 2.44772 17 3V6ZM18 8H6V20H18V8ZM9 11H11V17H9V11ZM13 11H15V17H13V11ZM9 4V6H15V4H9Z"></path></svg>
                </button>
            </li>
        `;

        cardListItems = cardListItems + cardListItem;
    }
    
    const cardList = $('#card__list');
    cardList.innerHTML = cardListItems;
}
```

## Remove Task

```js
// app.js
import { tasks } from "./storage.js";
import { $, updateUI } from "./utils.js";



function addTask() {
    const taskText = $('#card__input').value;
    const task = {
        id: tasks.length + 1,
        taskText
    }

    tasks.push(task);

    console.log(tasks);
    updateUI();
}

function removeTask(event) {
   if(event.target.tagName !== 'BUTTON') return;
    const id = Number(event.target.getAttribute('data-id'));
    
    for (const idx in tasks) {
        if (tasks[idx].id === id) {
            tasks.splice(idx, 1);
            break;
        }
    }
    console.log(tasks);
    updateUI();
}

$('#button-add').addEventListener('click', addTask);
$('#card__list').addEventListener('click', removeTask);


```

```js
// utils.js
import { tasks } from "./storage.js";

export function $(id) {
    return document.querySelector(id);
}

export function updateUI() {
    let cardListItems = '';

    for(const task of tasks) {
        const cardListItem = `
            <li class="card__list-item">
                ${task.taskText}
                <button data-id=${task.id} class="button button--danger" type="button">
                    <svg style="pointer-events: none;" height="16px" width="16px" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor"><path d="M17 6H22V8H20V21C20 21.5523 19.5523 22 19 22H5C4.44772 22 4 21.5523 4 21V8H2V6H7V3C7 2.44772 7.44772 2 8 2H16C16.5523 2 17 2.44772 17 3V6ZM18 8H6V20H18V8ZM9 11H11V17H9V11ZM13 11H15V17H13V11ZM9 4V6H15V4H9Z"></path></svg>
                </button>
            </li>
        `;

        cardListItems = cardListItems + cardListItem;
    }
    
    const cardList = $('#card__list');
    cardList.innerHTML = cardListItems;
}
```


## Next Improvements

1. Make UI Reposnsive
2. Fix UI Bugs
3. Fix CSS Sizings
4. Show Pop Up Message
5. Show Message When No Tasks Remaining
6. Show Pending Tasks Count
7. Dark Mode
8. i18N
