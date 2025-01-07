---
title: Task_string - invertCase()_1
draft: false
tags:
  - "#JavaScript"
  - "#taskJS"
  - "#string"
---
```js
/*
Реализуйте функцию, которая меняет в строке регистр каждой буквы на противоположный.
Функция должна возвращать полученный результат
*/

const invertCase = (str) => {
    let res = '';
    
    for(let i = 0; i < str.length; i++) {
        if(str[i].match(/[A-Z]/gm)) {
            res += str[i].toLowerCase();
        } else {
            res += str[i].toUpperCase()
        }
    }
     return res   
}

console.log(invertCase('Hello, World!')); // hELLO, wORLD!
console.log(invertCase('I loVe JS'));     // i LOvE js
```

___

[[011 Решение задач JS, TS и React|Назад]]