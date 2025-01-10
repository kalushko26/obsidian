---
title: Task_memo - memo()_0
draft: false
tags:
  - "#JavaScript"
  - "#taskJS"
  - "#memo"
  - "#unknownINC"
---
```js
// Написать функцию, которая мемоизирует ответы другой функции
function memo() {
    // code here
}

function getA(obj){
  console.log('getA call', obj.a)
  return obj.a
}

const memoGetA = memo(getA);

const a1 = {a: 1}
const a2 = {a: 2}
const a3 = {a: 1}

console.log(memoGetA(a1)); // getA call 1 \n 1
console.log(memoGetA(a2)); // getA call 2 \n 2
console.log(memoGetA(a1)); // 1
console.log(memoGetA(a3)); // 1
```

**Ответ

```js

```

___

[[011 Решение задач JS, TS и React|Назад]]