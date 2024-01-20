tags: #JavaScript #taskJS #itOne 
____

```js
// Что печатает цикл и как сделать нормально?
let i = 10;

while (--i) {
    setTimeout(() => {
      console.log(i);
    }, 0)
}
```

### Ответ

```js
// Что печатает цикл и как сделать нормально?
let i = 10;

while (--i) {
   const j = i
    setTimeout(() => {
      console.log(i);
       console.log(j);
    }, 0)
}
```

___
### [[011 Решение задач JS, TS и React|Назад]]