---
title: Task_object - sumDimensions()_1
draft: false
tags:
  - "#JavaScript"
  - "#taskJS"
  - "#object"
  - "#сбербанк"
---
```js
// Посчитать сумму по полю dimensions.width

const arr = [{
	{
		id: 1,
		dimensions: {
			width: 10,
			height: 20,
		},
	},
	{
		id: 2,
	},
	{
		dimensions: {
			width: 10,
			height: 15,
		},
	},
}]
```

**Ответ

```js
function dimensionsWidth(arr) {
    const res = [];

    for (let name of arr) {
        if (typeof name?.dimensions?.width == 'number') {
            res.push(name.dimensions.width)
        }
    }

    return res.reduce((acc, el) => {
        acc = acc + el
        return acc
    }, 0)
}

console.log(dimensionsWidth(arr))
```

___

[[011 Решение задач JS, TS и React|Назад]]