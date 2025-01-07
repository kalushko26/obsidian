---
title: Task_array - sumOfTwo()_1
draft: false
tags:
  - "#JavaScript"
  - "#taskJS"
  - "#array"
  - "#for"
  - "#сбербанк"
---
```js
// Реализуйте функцию, которая возвращает индексы двух чисел из массива,
// сумма которых равна заданному значению


function sumOfTwo(arr, target) {
 // Ваш код здесь
}


sumOfTwo([2, 7, 11, 15], 9); // [0,1]
```

**Ответ

```js
function sumOfTwo(arr, target) {
  let indexArr = [];

  for (let i = 0; i < arr.length; i++) {
    for (let j = i + 1; j < arr.length; j++) {
      if (arr[i] + arr[j] === target) {
        indexArr.push(i, j);
        break;
      }
    }
  }

  return indexArr;
}

console.log(sumOfTwo([2, 7, 11, 15], 9)); // [0, 1]
```

___

[[011 Решение задач JS, TS и React|Назад]]