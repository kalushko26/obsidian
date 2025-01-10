---
title: Что такое teardown -функция в Jest?
draft: false
tags:
  - testing
  - Jest
  - afterAll
  - afterEach
---
  `teardown-функция` — это функция, которая выполняется после завершения одного или нескольких тестовых сценариев. Она используется для очистки ресурсов и состояний, созданных во время теста, например, закрытия подключений к базе данных или очистки временных файлов. Jest предоставляет функции завершения, такие как `afterAll` и `afterEach`, для выполнения действий в разные моменты жизненного цикла теста.

Пример использования `afterEach` в Jest для очистки состояния после каждого теста:

```javascript
let counter = 0;

beforeEach(() => {
  counter = 0; // Инициализация перед каждым тестом
});

test('counter should be 1', () => {
  counter += 1;
  expect(counter).toBe(1);
});

test('counter should be 2', () => {
  counter += 2;
  expect(counter).toBe(2);
});

afterEach(() => {
  counter = 0; // Очистка после каждого теста
});
```

____

[[007 Jest, RTL|Назад]]