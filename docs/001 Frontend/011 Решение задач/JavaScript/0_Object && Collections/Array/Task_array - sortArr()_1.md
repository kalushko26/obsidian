---
title: Task_array - sortArr()_1
draft: false
tags:
  - "#JavaScript"
  - "#taskJS"
  - "#sort"
  - "#spread"
  - "#array"
  - "#SignalINC"
---
```
// Напишите функцию сортировки массива
// (исходный массив должен остаться без изменений)

const array = [1, 5, 2, 4, 3];
```

**Ответ

```js
const array = [1, 5, 2, 4, 3];

function sorted(array) {
  let newArr = [...array]
  return newArr.sort((a, b) => b - a)
}

console.log(sorted(array))
console.log(array)
```

___
[[011 Решение задач JS, TS и React|Назад]]