---
title: Task_string  - removeExclamation()_1
draft: false
tags:
  - JavaScript
  - "#taskJS"
  - "#райфайзенбанк"
  - "#string"
---
```js
const removeExclamation = (str, count) => {
// Ваш код здесь
};

 console.log(removeExclamation("!!He!!llo, !world!", 5));
```

**Ответ

```js
const removeExclamation = (str, count) => {
    if(typeof str !== 'string') {
        return undefined
    }
    
    let newStr = str;
    let removedCounter = 0;
    
    for(let i = 0; i < str.length; i++) {
        if(removedCounter === count){
            return newStr;
        } else if(str[i] === '!') {
            newStr = newStr.replace(str[i], '')
            removedCounter += 1
        }
    }
    
    return newStr
};

 console.log(removeExclamation("!!He!!llo, !world!", 5)); // Hello, world!

```

___

[[011 Решение задач JS, TS и React|Назад]]