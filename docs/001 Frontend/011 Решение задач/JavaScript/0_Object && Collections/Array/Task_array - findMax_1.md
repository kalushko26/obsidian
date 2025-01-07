---
title: Task_array - findMax_1
draft: false
tags:
  - "#JavaScript"
  - "#taskJS"
  - "#array"
  - "#sort"
  - "#SignalINC"
---
```
// Напишите функцию поиска максимального числа

const array2 = [1, 2, 3, 4, 5, 6];
```

**Ответ

```js
// Напишите функцию поиска максимального числа
const array = [1, 2, 3, 4, 5, 6];

function findMax(array) {
  return array.sort((a, b) => b - a)[0]
}

console.log(findMax(array))
```

___

[[011 Решение задач JS, TS и React|Назад]]