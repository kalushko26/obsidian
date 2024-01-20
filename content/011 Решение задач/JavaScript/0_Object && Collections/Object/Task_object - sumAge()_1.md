tags: #JavaScript #taskJS #object #recursion 
___

```js
function sumAge(user) {}

const user1 = {
    name: "Петр",
    age: 49,
    children: [
        {
            name: "Ника",
            age: 25,
            children: [
                {
                    name: "Андрей",
                    age: 3,
                },
                {
                    name: "Олег",
                    age: 1,
                },
            ],
        },
        {
            name: "Александр",
            age: 22,
        },
    ],
};

console.log(sumAge(user1)); // 100
```

### Ответ

```js
function sumAge(user) {
  let resAge = user.age;
  
  if(user.children){
    for(let i = 0; i < user.children.length; i++) {
      resAge = resAge + sumAge(user.children[i])
    }
  }

  return resAge;
}
```



___
### [[011 Решение задач JS, TS и React|Назад]]