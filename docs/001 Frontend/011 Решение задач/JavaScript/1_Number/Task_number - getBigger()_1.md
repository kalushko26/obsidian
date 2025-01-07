---
title: Task_number - getBigger()_1
draft: false
tags:
  - "#JavaScript"
  - "#taskJS"
  - "#number"
  - "#itOne"
---
```js
// на вход передано число, вернуть максимально возможное значение, составленное из цифр входящих в число

const getBigger = (number) => {
  // Ваш код здесь
}

console.log(getBigger(6291))
console.log(getBigger(417))
console.log(getBigger(3814));
```

**Ответ

```js
const getBigger = (number) => {
  return Number(
    number
      .toString()
      .split("")
      .sort((a, b) => b - a)
      .join("")
  );
};

console.log(getBigger(6291));
console.log(getBigger(417));
console.log(getBigger(3814));
```

___

[[011 Решение задач JS, TS и React|Назад]]