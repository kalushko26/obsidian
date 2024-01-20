tags: #JavaScript #taskJS #itOne 
____

```js
// создать массив: [0,1,2,3,4,5,6,7,8,9]
```

### Ответ

```js
const arr = Array.from({length: 10}, (__, i) => i)
// или:
const arr =[...Array(10).keys()]
```

___
### [[011 Решение задач JS, TS и React|Назад]]