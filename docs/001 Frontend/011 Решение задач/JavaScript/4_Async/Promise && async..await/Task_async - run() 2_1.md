---
title: Task_async - run() 2_1
draft: false
tags:
  - "#JavaScript"
  - "#taskJS"
  - "#async"
  - "#unknownINC"
---
```js
// необходимо дописать функцию в которой элементы массива будут
// последовательно выводится в консоль спустя промежуток времени 
// указанный в атрибуте  timeout

const run = arr =>{

}
const arr = [
  {name:'first', timeout:3000},
  {name:'second', timeout:5000},
  {name:'third', timeout:2000}
]

console.log(run(arr))
```

**Ответ

```js
const run = arr => {
  arr.forEach((item, index) => {
    setTimeout(() => {
      console.log(item.name);
    }, item.timeout);
  });
}

const arr = [
  {name:'first', timeout:3000},
  {name:'second', timeout:5000},
  {name:'third', timeout:2000}
];

run(arr);
```

___

[[011 Решение задач JS, TS и React|Назад]]