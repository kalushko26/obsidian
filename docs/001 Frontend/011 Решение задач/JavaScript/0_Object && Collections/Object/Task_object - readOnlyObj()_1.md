---
title: Task_object - readOnlyObj()_1
draft: false
tags:
  - "#JavaScript"
  - "#taskJS"
  - "#object"
  - "#Object-defineProperty"
  - "#SignalINC"
---
```js
const readOnlyObj = {
  name: "some string",
  age: ""
};

readOnlyObj.name = "";
```

**Ответ

```js
const readOnlyObj = {
  name: "some string",
  age: "",
};

Object.defineProperties(readOnlyObj, {
  name: {
    writable: false,
  },
})

readOnlyObj.name = "";
console.log(readOnlyObj.name)
```

___

[[011 Решение задач JS, TS и React|Назад]]