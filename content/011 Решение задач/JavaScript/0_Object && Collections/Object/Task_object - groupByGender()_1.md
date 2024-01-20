tags: #JavaScript #taskJS #object #unknownINC
____

```js
// Из исходного массива сделать объект, ключами которого будут все встречающиеся gender,
// а значениями массив объектов юзеров

const users = [
    {
        id: 1,
        name: "Виктория",
        gender: "female",
    },
    {
        id: 2,
        name: "Андрей",
        gender: "male",
    },
    {
        id: 3,
        name: "Александр",
        gender: "male",
    },
];

function groupByGender(users) {
 // Ваш код здесь
}

const groupedByGender = groupByGender(users);
console.log(groupedByGender);
```

### Ответ

```js
function groupByGender(users) {
  const gender = { female: [], male: [] };

  for (const user of Object.values(users)) {
    const { id, name, gender: userGender } = user;
    const res = { id, name };
    userGender === 'female' ? gender.female.push(res) : gender.male.push(res);
  }

  return gender;
}
```



___
### [[011 Решение задач JS, TS и React|Назад]]