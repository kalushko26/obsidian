---
title: Что возвращает fetch? Как получить содержимое ответа? Как обрабатывать ошибки?
draft: false
tags:
  - "#React"
  - "#fetch"
  - "#AJAX"
  - "#promise"
  - "#response"
  - "#reject"
info:
  - "[[0086 FETCH|Методы fetch()]]"
---
Метод `fetch()` возвращает Promise, который разрешается в объект Response, представляющий ответ на запрос. Для получения содержимого ответа можно использовать различные методы, такие как `json()`, `text()`, `arrayBuffer()`, `blob()`, в зависимости от типа данных, которые мы ожидаем получить в ответе.

Например, если мы ожидаем, что сервер вернет JSON-объект, мы можем получить его следующим образом:

```jsx
fetch("https://example.com/data.json")
  .then((response) => response.json())
  .then((data) => console.log(data))
  .catch((error) => console.error(error))
```

_Если в процессе выполнения запроса произойдет ошибка_ (например, сервер вернет код ошибки), _то Promise будет отклонен и мы можем обработать ошибку с помощью метода `catch()`._ В этом случае мы можем вывести сообщение об ошибке или выполнить другие действия, например, повторить запрос:

```jsx
fetch("https://example.com/data.json")
  .then((response) => {
    if (!response.ok) {
      throw new Error("Ошибка HTTP: " + response.status)
    }
    return response.json()
  })
  .then((data) => console.log(data))
  .catch((error) => console.error(error))
```

В этом примере мы проверяем код состояния HTTP-ответа, и если он не `ok` (не в диапазоне 200-299), мы выбрасываем исключение с сообщением об ошибке. В блоке `catch()` мы ловим это исключение и выводим сообщение об ошибке в консоль.

---

[[004 ReactCore|Назад]]