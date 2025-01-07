---
title: Task_array - arraySubset()_1
draft: false
tags:
  - "#JavaScript"
  - "#taskJS"
  - "#array"
---
```JS
/*
Напишите функцию, которая проверяет, является ли второй массив подмножеством первого. То есть есть ли элементы второго массива в первом.
*/

function arraySubset(source, subset) {
  // todo
}

console.log(arraySubset([2, 1, 3], [1, 2, 3])) // -> true
console.log(arraySubset([2, 1, 1, 3], [1, 2, 3])) // -> true
console.log(arraySubset([1, 1, 1, 3], [1, 3, 3])) // -> false
console.log(arraySubset([1, 2], [1, 2, 3])) // -> false
```

**Ответ

```js
function arraySubset(source, subset) {
  const sourceSet = new Set(source);
  for (let i = 0; i < subset.length; i++) {
    if (!sourceSet.has(subset[i])) {
      return false;
    }
    sourceSet.delete(subset[i]);
  }
  return true;
}
```

___

[[011 Решение задач JS, TS и React|Назад]]