---
title: Task_anagram - anagram()_1
draft: false
tags:
  - "#JavaScript"
  - "#taskJS"
  - "#anagram"
  - "#Яндекс"
---
```js
const anagram1 = ['cat', 'eat', 'tac', 'tae', 'tea', 'atc', 'act'];
const anagram2 = ['cat', 'eat', 'tac', 'tae', 'tea', 'atc', 'act', 'dft', 'ffg', 'gfg'];

const anagrams = (arr) => {
	// Ваш код здесь
}

console.log(anagrams(anagram1)); 
/* 
[
  ['cat', 'tac', 'atc', 'act'], 
  ['eat', 'tae', 'tea']
]
*/
console.log(anagrams(anagram2)); 
/*
[
  ['cat', 'tac', 'atc', 'act'], 
  ['eat', 'tae', 'tea'], 
  ['dft'], 
  ['ffg'], 
  ['gfg']
]
*/
```

**Ответ

```js
const anagram1 = ['cat', 'eat', 'tac', 'tae', 'tea', 'atc', 'act'];
const anagram2 = ['cat', 'eat', 'tac', 'tae', 'tea', 'atc', 'act', 'dft', 'ffg', 'gfg'];

const anagrams = (arr) => {
  let obj = {};

  for (let str of arr) {
    const diff = str.split('').sort().join('')
    obj[diff] ? obj[diff].push(str) : (obj[diff] = [diff])
  }

  return Object.values(obj)
}

console.log(anagrams(anagram1)); 
/* 
[
  ['cat', 'tac', 'atc', 'act'], 
  ['eat', 'tae', 'tea']
]
*/
console.log(anagrams(anagram2)); 
/*
[
  ['cat', 'tac', 'atc', 'act'], 
  ['eat', 'tae', 'tea'], 
  ['dft'], 
  ['ffg'], 
  ['gfg']
]
*/
```

___

[[011 Решение задач JS, TS и React|Назад]]