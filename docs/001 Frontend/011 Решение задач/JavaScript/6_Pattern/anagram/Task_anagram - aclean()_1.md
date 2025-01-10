---
title: Task_anagram - aclean()_1
draft: false
tags:
  - "#JavaScript"
  - "#taskJS"
  - "#anagram"
  - "#СравниРУ"
---
```js
/*
Анаграммы – это слова, у которых те же буквы в том же количестве, но они располагаются в другом порядке.

Например:
`nap - pan ear - are - era cheaters - hectares - teachers`

Напишите функцию `aclean(arr)`, которая возвращает массив слов, очищенный от анаграмм.
*/

let arr = ["nap", "teachers", "cheaters", "PAN", "ear", "era", "hectares"];

function aclean(arr){
	// Ваш код здесь
}

console.log(aclean(arr)); // "nap,teachers,ear" или "PAN,cheaters,era"
// Из каждой группы анаграмм должно остаться только одно слово, не важно какое.
```

**Ответ

```js
function aclean(arr) {
  let objAn = {};

  for (let words of arr) {
    let sorted = words.toLowerCase().split("").sort().join("");
    if (objAn[sorted]) {
      objAn[sorted].push(words);
    } else {
      objAn[sorted] = [words];
    }
  }
  let finished = [];
  let results = Object.values(objAn);

  for (let i = 0; i < results.length; i++) {
    finished.push(results[i][0])
  }

  return finished.join(',');
}
```

___

[[011 Решение задач JS, TS и React|Назад]]