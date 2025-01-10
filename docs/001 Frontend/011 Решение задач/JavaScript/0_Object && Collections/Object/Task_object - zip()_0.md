---
title: Task_object - zip()_0
draft: false
tags:
  - "#JavaScript"
  - "#taskJS"
  - "#object"
---

```js
const objects = [
    { foo: 5, bar: 6 },
    { foo: 13, baz: -1 }
];

function zip() {
	... ваш код здесь
}

console.log(zip(...objects)) ..


function zip () {
    if(arguments.length === 0) return
    else {
        let zipObj = {}
        let arrOfObj = Array.from(arguments)
        
        arrOfObj.forEach((obj) => {
            for(let key in obj) {
                if(!(zipObj[key])) {
                    zipObj[key] = obj[key]
                }
            }
        })
        
        return zipObj
    }
}
```

**Ответ

```js

```

___

[[011 Решение задач JS, TS и React|Назад]]