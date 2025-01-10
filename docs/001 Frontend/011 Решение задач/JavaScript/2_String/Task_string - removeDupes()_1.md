---
title: Task_string - removeDupes()_1
draft: false
tags:
  - "#JavaScript"
  - "#taskJS"
  - "#set"
---
```js
function removeDupes(str) {
// Ваш код здесь
}

console.log(removeDupes("abcd")); // -> 'abcd'
console.log(removeDupes("aabbccdd")); // -> 'abcd'
console.log(removeDupes("abcddbca")); // -> 'abcd'
console.log(removeDupes("abababcdcdcd")); // -> 'abcd'
```

**Ответ

```js
function removeDupes(str) {
	const uniqueCol = new Set(str)
	return [...uniqueCol].join('')
}

console.log(removeDupes("abcd")); // -> 'abcd'
console.log(removeDupes("aabbccdd")); // -> 'abcd'
console.log(removeDupes("abcddbca")); // -> 'abcd'
console.log(removeDupes("abababcdcdcd")); // -> 'abcd'
```

___

[[011 Решение задач JS, TS и React|Назад]]