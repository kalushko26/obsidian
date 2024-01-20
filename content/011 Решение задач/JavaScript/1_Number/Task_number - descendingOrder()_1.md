tags: #JavaScript #taskJS #number #домКлик
___

```js
/*
Ваша задача состоит в том, чтобы создать функцию,
которая может принимать любое не отрицательное целое число в качестве аргумента
и возвращать его с цифрами в порядке убывания.
По сути, переставьте цифры, чтобы получить максимально возможное число
*/

function descendingOrder(n) {
 // Ваш код здесь
}

console.log(descendingOrder(0) === 0)
console.log(descendingOrder(1) === 1)
console.log(descendingOrder(111) === 111)
console.log(descendingOrder(15) === 51)
console.log(descendingOrder(1021) === 2110)
console.log(descendingOrder(123456789) === 987654321)
```

### Ответ

```js
function descendingOrder(n) {
    if(typeof n !== 'number') return 'undefined'
    
    return Number(("" + n).split('').sort((a, b) => b - a).join(''))

}

console.log(descendingOrder(0) === 0)
console.log(descendingOrder(1) === 1)
console.log(descendingOrder(111) === 111)
console.log(descendingOrder(15) === 51)
console.log(descendingOrder(1021) === 2110)
console.log(descendingOrder(123456789) === 987654321)
```


___
### [[011 Решение задач JS, TS и React|Назад]]