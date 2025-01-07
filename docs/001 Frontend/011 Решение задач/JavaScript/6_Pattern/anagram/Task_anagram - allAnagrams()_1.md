---
title: Task_anagram - allAnagrams()_1
draft: false
tags:
  - "#JavaScript"
  - "#anagram"
  - "#taskJS"
  - "#СравниРУ"
---
```js
// Работать функция должна как показано в примере ниже:

function allAnagrams(array) {
// Код здесь
}

console.log(allAnagrams(["abcd", "bdac", "cabd"])); // true
console.log(allAnagrams(["abcd", "bdXc", "cabd"])); // false
```

**Ответ

```js
function allAnagrams(array) {
	let newArr = [];
	for (let i = 0; i < array.length; i++) {
		let newWords = array[i].split('').sort()
		newArr.push(newWords.join(''))
	}
	const uniqueArr = [...(new Set(newArr))]
	return true ? (uniqueArr.length === 1) : false
}

console.log(allAnagrams(["abcd", "bdac", "cabd"])); // true
console.log(allAnagrams(["abcd", "bdXc", "cabd"])); // false
```

___

[[011 Решение задач JS, TS и React|Назад]]