---
title: Task_array - sumValue()_1
draft: false
tags:
  - "#JavaScript"
  - "#taskJS"
  - "#array"
  - "#reduce"
  - "#object"
  - "#сбербанк"
---
```js
const arr = [1, 2, 3, 4, 4]; // '1:1, 2:1, 3:1, 4:2'

function objSum(arr) {
 // Ваш код здесь
}

console.log(objSum(arr)); // {'1:1, 2:1, 3:1, 4:2'}
```

**Ответ

```js
function objSum(arr) {

  return arr.reduce((acc, el) => {
    acc[el] = (acc[el] | 0) + 1 
    return acc
  }, {})
}

console.log(objSum(arr)); // {'1:1, 2:1, 3:1, 4:2'}
```

___

[[011 Решение задач JS, TS и React|Назад]]