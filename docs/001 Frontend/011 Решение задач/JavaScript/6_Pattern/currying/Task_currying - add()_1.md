---
title: Task_currying - add()_1
draft: false
tags:
  - "#JavaScript"
  - "#currying"
  - "#taskJS"
---
```js
// Напишите функцию, которая складывает 2 числа.
// Работать функция должна как показано в примере ниже:

let add = function (a = 0) {
 // Ваш код здесь
}

console.log(add(1)(2)(3)()); // 6
console.log(add(1)(2)()); // 3
```

**Ответ

```js
function add(a = 0) {
	let sum = a;
	const res = (b) => {
		if(typeof b === 'undefined') return sum
		sum += b;
		return res
	}
	return res
}

console.log(add(1)(2)(3)()) // 6
console.log(add(1)(2)()) // 3
```

___

[[011 Решение задач JS, TS и React|Назад]]