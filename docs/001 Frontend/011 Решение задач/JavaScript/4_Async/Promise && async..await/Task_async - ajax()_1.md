---
title: Task_async - ajax()_1
draft: false
tags:
  - "#JavaScript"
  - "#taskJS"
  - "#promise"
  - "#сбербанк"
  - "#itOne"
---
```js 
// Можем работать только с array, длина его неизвестна:
const array = [ajax, ajax, ajax, ..., ajax]

// Что должны получить?
Promise.resolve()
	.then(array[0]) // 15:00:00
	.then(array[1]) // 15:00:01
	.then(array[2]) // 15:00:02
	.then(array[3]) // 15:00:03
	.then(array[4]) // 15:00:04

// Код пишем ниже:
```

**Ответ

```js
const array = [ajax1, ajax2, ajax3, /* ... */, ajaxN];

// Функция для выполнения асинхронной операции по индексу в массиве
const executeAsyncOperation = (index) => {
  if (index >= array.length) {
    return Promise.resolve(); // Возвращаем завершенный промис, если достигнут конец массива
  }
  
  const asyncOperation = array[index];
  
  return asyncOperation() // Выполняем асинхронную операцию
    .then(() => {
      // Переходим к следующей операции с увеличением индекса
      return executeAsyncOperation(index + 1);
    });
};

// Запускаем выполнение операций, начиная с первого элемента массива
executeAsyncOperation(0)
  .then(() => {
    console.log('Все операции завершены');
  })
  .catch((error) => {
    console.error('Произошла ошибка:', error);
  });
```

___

[[011 Решение задач JS, TS и React|Назад]]