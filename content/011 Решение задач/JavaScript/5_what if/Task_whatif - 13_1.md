tags: #JavaScript #taskJS #itOne 
____

```js
// Достать width с помощью диструктуризации
const product = {
    price: 3990,
    options: [
        {
            id: 1,
            title: '256ГБ',
            price: 450,
        },
        {
            id: 2,
            title: '512ГБ',
            price: 990,
        }
    ],
    info: {
        screen: {
            size: {
                width: 1920,
                height: 1080
            }
        }
    }
}
```

### Ответ

```js
 const {info: {screen: {size: {width}}}} = product;
console.log(width);
```

___
### [[011 Решение задач JS, TS и React|Назад]]