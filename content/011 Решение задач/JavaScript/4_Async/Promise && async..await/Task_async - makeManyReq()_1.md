tags: #JavaScript #taskJS #promise #promiseAllSettled #технологияДоверия 
____

```js
// Дан список ссылок и функция запроса
// Необходимо реальзовать процедуру запроса всех сылок из списка
// если одна ссылка выполнится с ошибкой то вернется ошибка,


function makeManyReq() {
    const urls = ["https://yandex.ru", "https://mail.ru", "https://rambler.ru"];

    function fetchUrl(url) {
        return Promise.resolve(`Succses ${url}`);
    }

    // Ваш код здесь

}
```

### Ответ

```js
    // тогда нужно использовать allSettled
    
function makeManyReq() {
  const urls = ["https://yandex.ru", "https://mail.ru", "https://rambler.ru"];

  function fetchUrl(urls) {
      return Promise.resolve(`Succses ${urls}`);
  }
  const answer = urls.map((el) => fetchUrl(el))

  Promise.allSettled(answer).then(console.log).catch(console.error)
}

makeManyReq()
```


___
### [[011 Решение задач JS, TS и React|Назад]]