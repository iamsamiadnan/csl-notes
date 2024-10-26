In simple terms, a function in programming is like a recipe that you can use repeatedly. It’s a set of instructions that performs a specific task. You give it some input (ingredients), it processes them, and then it gives back an output (result). 

1. I may need the return value
2. I don't care of the return value

## Basic Syntax
```js
function func-name(param-list) {
	// do something ...;
	return something ...;
}

// 2
function func() {
	console.log('Hello');
}
func();

// 3
function func() {
	return 'Hello';
}
const a = func();
console.log(a);

// 4
function func(message) {
	console.log(message);
}
func('Hello there. ..');


```
## Blender Function Example
```js
function blender(fruit) { // fruit param is only available in { }
	return `${fruit} juice!`;
}

const glass = blender('🍎');
console.log(glass);
```
## Black Tea Function Example
```js
function makeBlackTea() {
	console.log('Boiling water ...');
	console.log('Placing black tea in the cup.');
	console.log('Pouring water, steeping, and removing tea.');
	console.log(`Adding 1 teaspoon(s) of sugar.`); 
}

makeBlackTea();
```
## Greet Function
```js
function greet(name) {
	console.log('Hello ${name}!');
}

greet('Sami');
greet(); // undefined

function greet(name) {
	return 'Hello ${name}!;
}

console.log(greet('Sami')); // undefined
```
## Tea Function With Parameter
```js
function makeTea(type, sugar, hasMilk) {
	console.log('Boiling water ...');
	console.log('Placing ${type} tea in the cup.');
	console.log('Pouring water, steeping, and removing tea.');

	if (sugar > 0) console.log(`Adding ${sugar} teaspoon(s) of sugar.`); 
	if (hasMilk) console.log('Adding milk.');
}

makeTea('green', 1, true);
```
## Square Function
```js
function square(num) {
	const sqr = num * num;
	return sqr;
}

const result = square(5);
console.log(result);

```
## Multiple Parameter
```js
function add(num1, num2) {
	return num1 + num2;
}

console.log(add(2, 3));
console.log(add(2)); // NaN
```
## Profit Calculator Using Function
```js
function calcProfit(buyingPrice, sellingPrice) {
	const profit = sellingPrice - buyingPrice;
	return profit;
}

const bPrice = 100;
const sPrice = 120;

const profit = calcProfit(bPrice, sPrice);
console.log(`My Profit: ${profit}`);
```
##
```js
function func() {
	return 'Hello ...'; // returns to caller
	console.log('Bonjour ! ...'); // ignores
}

func();
```
## Ludo Example
```js
function isEven(num) {
	if(num % 2 === 0) return true;
	else return false; 
	// if not return false explicitly, the function will return undefined.
}

/*
function isEven(num) {
	if(num % 2 === 0) return true;
}
*/

/*
function isEven(num) {
	return num % 2 === 0;
}
*/

const playerCount = 2;

if(isEven(playerCount)) {
	console.log("Let's Play!");
}
else {
	console.log("Not Allowed!");
}

```
## getFullName() Function
```js
function getFullName(employee) {
	const firstName = employee.firstName;
	const lastName = employee.lastName;
	const fullName = firstName + ' ' + lastName;
	return fullName;
}
/*
function getFullName(employee) {
	return `${employee.firstName} ${employee.lastName}`;
}
*/

const employee = {
	firstName: 'Adnan',
	lastName: 'Sami',
}

const fullName = getFullName(employee);
console.log(`Hello, ${fullName}`);

```
## Passing Array
```js
function countElements(numbersArray) {
	const length = numbersArray.length;
	return length;
}

const result = countElements([1, 3, 4, 5, 67]);
console.log(result);
```
## Add Numbers Function
```js
function addNumbers(numbers) {
	let sum = 0;
	for(const num of numbers) {
		sum = sum + num;
	}

	return sum;
}

const numbers = [1, 2, 3, 4];
const result = addNumbers(numbers);
console.log(result);
```


send cv
playing competative game
error handling
import export
how can I return multiple value from a function