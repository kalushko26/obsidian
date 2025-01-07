---
title: Task_whatif - 16_1
draft: false
tags:
  - "#JavaScript"
  - "#taskJS"
  - "#itOne"
---
```js
// Избавиться от лишних меседжей
useEffect(() => {
    if (!message) {
        return
    }
    const pauseID = setTimeout(() => {
        setMessage('');
    }, 7000);


}, [message]);
```

**Ответ

```js
// Избавиться от лишних меседжей
useEffect(() => {
    if (!message) {
        return
    }
    const pauseID = setTimeout(() => {
        setMessage('');
    }, 7000);
 return () => clearTimeout(pauseID)
}, [message]);
```

___

[[011 Решение задач JS, TS и React|Назад]]