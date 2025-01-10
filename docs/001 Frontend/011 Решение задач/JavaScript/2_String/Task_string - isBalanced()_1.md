---
title: Task_string - isBalanced()_1
draft: false
tags:
  - "#JavaScript"
  - "#taskJS"
  - "#RegExp"
  - "#string"
  - "#БэллИнтегратор"
  - "#сбербанк"
  - "#Яндекс"
  - "#itOne"
---
```js
function isBalanced(str) {
	// Ваш код здесь
}

console.log(isBalanced("(x + y) - (4)")); // -> true
console.log(isBalanced("(((10 ) ()) ((?)(:)))")); // -> true
console.log(isBalanced("[({()})]")); // -> true
console.log(isBalanced("(50)((")); // -> false
console.log(isBalanced("[{]}")); // -> false
```

**Ответ

```js
function isBalanced(str) {
  const regProps = /[\(\)|\[\]|\{\}]/gm;
  const regArrows = /\(\)|\[\]|\{\}/gm;

  let prev = '';
  let replaced = str.match(regProps).join('');

  while(replaced !== prev) {
    prev = replaced;
    replaced = replaced.replace(regArrows, '')
  }

  return prev === ''
}

console.log(isBalanced("(x + y) - (4)")); // -> true
console.log(isBalanced("(((10 ) ()) ((?)(:)))")); // -> true
console.log(isBalanced("[({()})]")); // -> true
console.log(isBalanced("(50)((")); // -> false
console.log(isBalanced("[{]}")); // -> false
```

___

[[011 Решение задач JS, TS и React|Назад]]