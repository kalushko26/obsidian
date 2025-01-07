---
title: Task_object - removeC()_1
draft: false
tags:
  - "#JavaScript"
  - "#taskJS"
  - "#object"
  - "#unknownINC"
---
```js
const obj = { a: 1, b: 2, f: '33', d: '4', r: {c: 'rwerw', f: { a: 1, c: 3}} };

// Необходимо написать функцию, которая на вход принимает объект и возвращает новый объект без свойства c - 2 варианта
 
const removeC = (obj) => {
 // Ваш код здесь
};

removeC(obj)
```

**Ответ

```js
const removeC = (obj) => {
  const newObj = {};
  for (let el in obj) {
    if (el == "c") {
      continue;
    }

    if (typeof obj[el] == "object") {
      newObj[el] = removeC(obj[el]);
    } else {
      newObj[el] = obj[el];
    }
  }
  return newObj;
};
```

___

[[011 Решение задач JS, TS и React|Назад]]