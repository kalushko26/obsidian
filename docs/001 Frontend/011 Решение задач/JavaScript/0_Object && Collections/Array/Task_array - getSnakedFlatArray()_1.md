---
title: Task_array - getSnakedFlatArray()_1
draft: false
tags:
  - "#JavaScript"
  - "#taskJS"
  - "#array"
  - "#СИБУР"
---
```js
// Реальзовать функцию, которая будет в консоль выводить значения элементов по спирали. Например из arr1 в консоли будет 1 2 3 4 5 6 7 ... 20

const arr1 = [
  [1, 2, 3, 4, 5],
  [14, 15, 16, 17, 6],
  [13, 20, 19, 18, 7],
  [12, 11, 10, 9, 8]
];

const getSnakedFlatArray = () => {
  // Code here
};

// console.log(getSnakedFlatArray(arr1));
```

**Ответ

```js
function printSpiralArray(arr) {
	let result = [];

	while (arr.length) {
		result.push(...arr.shift());
		for (let i = 0; i < arr.length; i++) {
			result.push(arr[i].pop());
		}
		if (arr.length) {
			result.push(...arr.pop().reverse());
		}
		for (let i = arr.length - 1; i >= 0; i--) {
			if (arr[i].length) {
				result.push(arr[i].shift());
			}
		}
	}
	console.log(result.join(' '));
}

const arr = [
	[1, 2, 3, 4, 5],
	[14, 15, 16, 17, 6],
	[13, 20, 19, 18, 7],
	[12, 11, 10, 9, 8]
];

printSpiralArray(arr);
```

___

[[011 Решение задач JS, TS и React|Назад]]