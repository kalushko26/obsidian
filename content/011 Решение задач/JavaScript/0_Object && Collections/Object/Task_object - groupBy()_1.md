tags: #JavaScript #taskJS #object #forEach #unknownINC 
___

```js
// Вызов функции - groupBy(persons, "age") 

const persons = [
  { name: 'Alex', age: 20 },
  { name: 'Lena', age: 25 },
  { name: 'Pavel', age: 20 }
]

function groupBy(arr, prop) {
 // Ваш код здесь
}


console.log(groupBy(persons, 'age'))

// Результат {
//   20: [{ name: 'Alex', age: 20 }, { name: 'Pavel', age: 20 } ],
//   25: [{ name: 'Lena', age: 25 }]
// }
```

### Ответ

```js
function groupBy(arr, prop) {
  let groupRes = {}
  
  arr.forEach(el => {
    const {name, age} = el

    if (groupRes[age]) {
      groupRes[age].push({ name, age });
    } else {
      groupRes[age] = [{ name, age }];
    }
  });
  return groupRes
}

console.log(groupBy(persons, 'age'))
```

___
### [[011 Решение задач JS, TS и React|Назад]]