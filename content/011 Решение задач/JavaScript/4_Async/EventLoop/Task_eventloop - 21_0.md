tags: #JavaScript #taskJS #EventLoop 
___

```js
//! будет ли обработан ответ?

fetch('http://www.speedtest.net')
    .then(function (response) {
        console.log(response);
    })
    .catch(function (error) {
        console.error(error);
    });
while (true) console.log(1);
```


___
### [[011 Решение задач JS, TS и React|Назад]]