---
title: Что такое JSX в TypeScript? Какие режимы JSX поддерживает TypeScript?
draft: false
tags:
  - "#TypeScript"
  - "#JSX"
  - "#React"
  - "#Preverse"
info:
---
`JSX` - это расширение языка JavaScript, которое позволяет использовать синтаксис XML для создания и манипулирования элементами пользовательского интерфейса. JSX используется в React для описания компонентов пользовательского интерфейса.

В TypeScript, *JSX поддерживается с помощью дополнительных опций компилятора, которые позволяют использовать JSX-синтаксис в файлах TypeScript. Для этого необходимо установить опцию `jsx` в значение `react` или `preserve`.*

1.  *Режим React* - это режим, в котором TypeScript транслирует JSX в вызовы функций React.createElement(). Этот режим поддерживается по умолчанию в TypeScript при использовании React.

```tsx
// Пример использования JSX в режиме react

import React from 'react';

type Props = {
  message: string;
};

const MyComponent = (props: Props) => {
  return <div>{props.message}</div>;
};
```

2.  *Режим preserve* - это режим, в котором TypeScript сохраняет JSX-синтаксис в выходном коде без трансформации. В этом режиме, JSX-элементы остаются как есть и могут быть обработаны другими инструментами.

```tsx
// Пример использования JSX в режиме preserve

type Props = {
  message: string;
};

const MyComponent = (props: Props) => {
  return <div>{props.message}</div>;
};
```

В обоих режимах можно использовать дженерики (`<>`), атрибуты (`className`, `style`, `onClick` и т.д.), шаблонные строки и другие возможности JSX.

*Для использования JSX в TypeScript также необходимо установить соответствующую библиотеку типов, например, `@types/react` для использования JSX в React.*

_____

[[005 TypeScript|Назад]]