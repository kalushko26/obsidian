tags: #JavaScript #taskJS #object #filter #sort #reduce #itOne #сбербанк 
___

```js
// сконкатенировать по value, expired не должны быть true, порядок отсортирован по order

const input = [
  {value: 'abcd', order: 4, expired: false},
  {value: 'qwer', order: 2, expired: true},
  {value: 'xyz1', order: 1, expired: false},
  {value: 'abx2', order: 3, expired: false},
]

function inputExpiredSort(data) {
	// Ваш код здесь
}

inputExpiredSort(input);
```

### Ответ

```js
function inputExpiredSort(data) {
  const filtered = data.filter((el) => !el.expired);
  const sorted = filtered.sort((a, b) => a.order - b.order);

  return sorted.reduce((acc, el) => {
    return acc + el.value;
  }, "");
}

console.log(inputExpiredSort(input));
```


___
### [[011 Решение задач JS, TS и React|Назад]]