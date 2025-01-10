---
title: Task_string - minifyString()_1
draft: false
tags:
  - "#JavaScript"
  - "#taskJS"
  - "#райфайзенбанк"
  - "#string"
---
```js
const minifyString = (string) => {
// your code here...
};

 console.log(minifyString("aaaawwwweerrr")); // '3a4w2e3r'
```

**Ответ

```js
const minifyString = (str) => {
    let res = '';
    
    const newObj = str.split('').reduce((acc, el) => {
        acc[el] = (acc[el] || 0) + 1
        return acc
    }, {})

    const newArr = Object.entries(newObj);
    
    for (let i = 0; i < newArr.length; i++) {
        res += newArr[i][1] + newArr[i][0];
    }
    
    return res;
};

console.log(minifyString("aaaawwwweerrr")); // '4a4w2e3r'
```

___

[[011 Решение задач JS, TS и React|Назад]]