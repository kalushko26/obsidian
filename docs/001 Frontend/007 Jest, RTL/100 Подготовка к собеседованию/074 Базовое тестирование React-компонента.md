---
title: Базовое тестирование React-компонента
draft: false
tags:
  - testing
  - Jest
  - react-testing-library
info:
  - https://habr.com/ru/companies/timeweb/articles/670480/
---
Для базового тестирования React-компонента с использованием Jest и React Testing Library (RTL) вам нужно:

Пример компонента:

```javascript
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p data-testid="count">{count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}

export default Counter;
```

Пример теста:

```javascript
import React from 'react';
import { render, screen, fireEvent } from '@testing-library/react';
import Counter from './Counter';

it('renders initial count and increments on button click', () => {
  // Рендерим компонент
  render(<Counter />);

  // Находим элементы
  const countElement = screen.getByTestId('count');
  const incrementButton = screen.getByText('Increment');

  // Проверяем начальное состояние
  expect(countElement).toHaveTextContent('0');

  // Имитируем клик по кнопке
  fireEvent.click(incrementButton);

  // Проверяем, что счетчик увеличился
  expect(countElement).toHaveTextContent('1');

  // Имитируем еще один клик
  fireEvent.click(incrementButton);

  // Проверяем, что счетчик увеличился еще раз
  expect(countElement).toHaveTextContent('2');
});
```

Пояснение:

1. **Импорт необходимых модулей**: Импортируйте `render`, `screen`, `fireEvent` и компонент `Counter`.
2. **Рендеринг компонента**: Используйте `render` для рендеринга компонента `Counter`
3. **Поиск элементов**: Используйте `screen.getByTestId` и `screen.getByText` для поиска элементов в DOM.
4. **Проверка начального состояния**: Используйте `expect` и методы Jest для проверки начального состояния компонента.
5. **Имитация взаимодействия**: Используйте `fireEvent.click` для имитации клика по кнопке.
6. **Проверка результатов**: Используйте `expect` для проверки, что компонент реагирует на взаимодействие правильно.

____

[[007 Jest, RTL|Назад]]
