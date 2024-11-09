```js
const numbers = [11, 22, 34, 56, 78, 88];

function doubleIt(number) {
	return number * 2;
}

const result = numbers.map(doubleIt);

console.log(result);
```

The `map` function in JavaScript is used to apply a specific function to each element in an array and create a new array with the results.

Here’s a breakdown of how `map` works with your code:

1. **Original Array**: You have an array, `numbers`, which contains `[11, 22, 34, 56, 78, 88]`.

2. **Mapping Function**: You define a function called `doubleIt`, which takes a `number` as input and returns `number * 2`. This function will be applied to each element of `numbers`.

3. **Using `map`**: The `map` function iterates over each element in `numbers` and applies `doubleIt` to each element:
   - For `11`, `doubleIt(11)` returns `22`
   - For `22`, `doubleIt(22)` returns `44`
   - And so on...

4. **Result**: The `map` function returns a new array with these transformed values: `[22, 44, 68, 112, 156, 176]`.

5. **Logging the Output**: Finally, `console.log(result);` outputs `[22, 44, 68, 112, 156, 176]`.

So, `map` works by creating a new array where each element is the result of applying a function (here, `doubleIt`) to the elements of the original array. 

Here's a visualization:

```plaintext
Original: [11, 22, 34, 56, 78, 88]
Mapped:   [22, 44, 68, 112, 156, 176]
```

The original `numbers` array remains unchanged.