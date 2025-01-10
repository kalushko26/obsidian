---
title: Какую функцию выполняет toHaveBeenCalledWith()?
draft: false
tags:
  - testing
  - Jest
  - toHaveBeenCalledWith
---
`toHaveBeenCalledWith` — это матчер, который используется для проверки того, был ли вызван мок-функция (mock function) с определенными аргументами. Он полезен при тестировании функций, которые вызывают другие функции, чтобы убедиться, что они вызываются с правильными параметрами.

Пример использования:
```javascript
test('mock function should be called with specific arguments', () => {
  const mockFn = jest.fn();

  mockFn('arg1', 'arg2');

  expect(mockFn).toHaveBeenCalledWith('arg1', 'arg2'); // Пройдет, так как mockFn была вызвана с 'arg1' и 'arg2'
});
```

В этом примере `mockFn` вызывается с аргументами `'arg1'` и `'arg2'`, и `toHaveBeenCalledWith` проверяет, что это действительно произошло.

____

[[007 Jest, RTL|Назад]]