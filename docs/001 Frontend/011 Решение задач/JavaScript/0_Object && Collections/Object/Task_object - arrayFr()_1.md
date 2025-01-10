---
title: Task_object - arrayFr()_1
draft: false
tags:
  - "#JavaScript"
  - "#taskJS"
  - "#object"
  - "#SignalINC"
---
```js
// Напишите функцию которая возвращает массив значение свойств объекта

const obj = {
  a: 1,
  b: 3,
  c: 2,
}

function arrayFr(obj) {
 // Ваш код здесь
}
```

**Ответ

```js
const obj = {
  a: 1,
  b: 3,
  c: 2,
}

function arrayFr(obj) {
  return Object.values(obj);
}

console.log(arrayFr(obj))
```

___

[[011 Решение задач JS, TS и React|Назад]]