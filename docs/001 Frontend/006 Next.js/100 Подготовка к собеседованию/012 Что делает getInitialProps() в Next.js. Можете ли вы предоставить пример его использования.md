---
title: Что делает `getInitialProps()` в Next.js? Можете ли вы предоставить пример его использования?
draft: false
tags:
  - NextJS
  - getInitialProps
  - SSR
info:
  - https://nextjs.org/docs/pages/api-reference/functions/get-initial-props
---
`getInitialProps` — это статический асинхронный метод в Next.js, который позволяет выполнять рендеринг на стороне сервера (SSR) для страницы. Он извлекает данные, необходимые для рендеринга страницы, и возвращает объект, который заполняет пропсы компонента.

Пример использования `getInitialProps` может быть таким: предположим, у вас есть страница профиля пользователя, которая должна отображать информацию о конкретном пользователе. `getInitialProps` может извлечь эти данные на основе идентификатора пользователя, переданного через параметры URL. 

Вот упрощенный пример:

```javascript
import React from 'react';

const UserProfile = ({ userData }) => {
  return (
    <div>
      <h1>{userData.name}</h1>
      <p>{userData.bio}</p>
    </div>
  );
};

UserProfile.getInitialProps = async ({ query }) => {
  const response = await fetch(`https://api.example.com/user/${query.id}`);
  const userData = await response.json();
  return { userData };
};

export default UserProfile;
```

В этом коде `getInitialProps` использует параметр `id` из URL для выполнения запроса к конечной точке API и получения соответствующих данных пользователя. Эти данные затем возвращаются в виде объекта, который становится пропсами компонента `UserProfile`, позволяя отобразить детали пользователя на стороне сервера.

___

[[006 Next.js|Назад]]