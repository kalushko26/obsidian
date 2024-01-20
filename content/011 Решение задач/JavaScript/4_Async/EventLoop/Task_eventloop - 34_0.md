tags: #JavaScript #taskJS #EventLoop 
____

```JS
console.log(1);

const promise1 = Promise.resolve().then(() => {
    console.log(2);
    setTimeout(() => console.log(3), 0)
});

const timer1 = setTimeout(() => {
    console.log(4)
    Promise.resolve().then(() => console.log(5))
}, 0)

console.log(6);
```

___
### [[011 Решение задач JS, TS и React|Назад]]
