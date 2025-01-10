---
title: Task_polyfill - some()_1
draft: false
tags:
  - "#JavaScript"
  - "#taskJS"
  - "#polyfill"
  - "#some"
  - "#альфабанк"
---
```js
// Условие: написать полифил для метода some
// [2, 5, 8, 1, 4].some((element) => element > 10); ---> false
// [12, 5, 8, 1, 4].some((element) => element > 10); ---> true

Array.prototype.mySome = function(cb) {
	// Ваш код здесь
}
```

**Ответ

```javascript
// Условие: написать полифил для метода some
// [2, 5, 8, 1, 4].some((element) => element > 10); ---> false
// [12, 5, 8, 1, 4].some((element) => element > 10); ---> true

Array.prototype.mySome = function(cb) {
	for (let i = 0; i < this.length; i++) {
		if(cb(this[i], i, this)){
		return true
		}
	}
	return false
} 
```

```js
Array.prototype.mySome = mySome

function mySome(cb) {
  for(let i = 0; i < this.length; i++) {
      if(cb(this[i])) {
          return true
      }
  }
  return false
}

[2, 5, 8, 1, 4].mySome(element => element > 10) // false
[2, 5, 8, 1, 4].mySome(element => element < 10) // true
```

___

[[011 Решение задач JS, TS и React|Назад]]