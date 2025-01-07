---
title: registerServiceWorker()
draft: false
tags:
  - React
  - registerServiceWorker
info:
  - https://habr.com/ru/companies/ruvds/articles/349858/
---
## Коротко о...

#registerServiceWorker - это функция, предоставляемая библиотекой #React, которая *позволяет зарегистрировать Service Worker* в приложении React.

`Service Worker` - это скрипт, который работает в фоновом режиме и может использоваться *для кэширования ресурсов, таких как стили, изображения и скрипты, что может улучшить производительность и быстродействие вашего приложения.*

Функция *`registerServiceWorker` вызывается в файле index.js* вашего приложения React, и *она регистрирует Service Worker, если он поддерживается браузером, который используется для запуска приложения.* При регистрации Service Worker также *создается кэш для ресурсов, которые могут быть использованы в офлайн-режиме.*

Зарегистрированный *Service Worker может слушать события жизненного цикла приложения, такие как установка, активация и обновление, и выполнять соответствующие действия в зависимости от этого.*

## Преимущества 

Вот несколько преимуществ использования Service Worker в приложении:

1.  *Офлайн-доступ:* Service Worker может кэшировать ресурсы, такие как изображения, стили и скрипты, что позволяет приложению работать в офлайн-режиме без доступа к интернету.
2.  *Улучшенная производительность:* Кэширование ресурсов позволяет уменьшить количество запросов к серверу, что улучшает производительность приложения и уменьшает время загрузки страницы.
3.  *Локальное хранение данных:* Service Worker может использоваться для локального хранения данных, что позволяет быстро получать данные, не обращаясь к серверу.
4.  *Push-уведомления:* Service Worker может использоваться для отправки push-уведомлений на устройство пользователя, что позволяет приложению своевременно уведомлять пользователя о важных событиях.
5.  *Улучшенная безопасность:* Service Worker может использоваться для проверки запросов на безопасность и блокировки запросов, которые могут представлять угрозу для безопасности приложения.
6.  *Актуализация данных:* Service Worker может использоваться для актуализации данных, когда приложение работает в фоновом режиме. Это позволяет приложению быстро получать обновленные данные, без необходимости обновлять страницу.

В целом, использование Service Worker может значительно улучшить производительность, функциональность и безопасность вашего приложения, а также обеспечить более плавный и удобный пользовательский опыт.

## Ограничения

Хотя Service Worker предоставляет множество преимуществ для разработки веб-приложений, есть несколько ограничений, которые нужно учитывать:

1.  *Ограничения безопасности:* Service Worker может работать только на HTTPS или на локальном хосте. Это сделано для обеспечения безопасности пользователей, так как Service Worker имеет доступ к чувствительным данным, таким как информация о куки и личные данные.
2.  *Ограничения кэширования:* Service Worker может кэшировать только те ресурсы, которые запрашивает само приложение. Это означает, что если ресурс запрашивается напрямую из браузера, то Service Worker не сможет его кэшировать.
3.  *Ограничения на обработку запросов:* Service Worker не может обрабатывать запросы, которые проходят через другие прокси и серверы кроме браузера, такие как запросы из расширений или из других приложений.
4.  *Ограничения на доступность API:* Service Worker не имеет доступа к некоторым API браузера, таким как DOM API. Это означает, что Service Worker не может изменять содержимое страницы напрямую.
5.  *Ограничения на работу с кэшем:* Service Worker может кэшировать только те ресурсы, которые определены в его области видимости. Если Service Worker находится в другой области, то он не сможет получить доступ к кэшу, созданному другим Service Worker.
6.  *Ограничения на поддержку браузеров:* Некоторые старые браузеры не поддерживают Service Worker, что означает, что приложение может не работать на этих браузерах или работать с ограниченной функциональностью.

В целом, Service Worker имеет некоторые ограничения, но они не являются серьезными препятствиями для использования этой технологии в создании веб-приложений.

## Пример

Конкретный пример инициализации `registerServiceWorker()` может выглядеть следующим образом:

```jsx
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';
import * as serviceWorker from './serviceWorker';

ReactDOM.render(<App />, document.getElementById('root'));

serviceWorker.register();
```

В этом примере мы импортируем компонент `App` и функцию `register()` из модуля `serviceWorker`, который был создан при инициализации приложения. Затем мы рендерим наше приложение, используя `ReactDOM`, и вызываем `register()` для регистрации Service Worker.

Обратите внимание, что вызов `register()` не требует аргументов, так как все необходимые параметры передаются через настройки Service Worker, которые определены в файле `serviceWorker.js`.

```jsx
// serviceWorker.js

const isLocalhost = Boolean(
  window.location.hostname === 'localhost' ||
    window.location.hostname === '[::1]' ||
    window.location.hostname.match(
      /^127(?:\.(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)){3}$/
    )
);

export function register() {
  if ('serviceWorker' in navigator) {
    const publicUrl = new URL(process.env.PUBLIC_URL, window.location.href);
    if (publicUrl.origin !== window.location.origin) {
      return;
    }

    window.addEventListener('load', () => {
      const swUrl = `${process.env.PUBLIC_URL}/service-worker.js`;

      if (isLocalhost) {
        checkValidServiceWorker(swUrl);
      } else {
        registerValidSW(swUrl);
      }
    });
  }
}

function registerValidSW(swUrl) {
  navigator.serviceWorker
    .register(swUrl)
    .then(registration => {
      registration.onupdatefound = () => {
        const installingWorker = registration.installing;
        if (installingWorker == null) {
          return;
        }
        installingWorker.onstatechange = () => {
          if (installingWorker.state === 'installed') {
            if (navigator.serviceWorker.controller) {
              console.log('New content is available; please refresh.');
            } else {
              console.log('Content is cached for offline use.');
            }
          }
        };
      };
    })
    .catch(error => {
      console.error('Error during service worker registration:', error);
    });
}

function checkValidServiceWorker(swUrl) {
  fetch(swUrl)
    .then(response => {
      if ( 
        response.status === 404 ||
        response.headers.get('content-type').indexOf('javascript') === -1
      ) {
        navigator.serviceWorker.ready.then(registration => {
          registration.unregister().then(() => {
            window.location.reload();
          });
        });
      } else {
        registerValidSW(swUrl);
      }
    })
    .catch(() => {
      console.log(
        'No internet connection found. App is running in offline mode.'
      );
    });
}

export function unregister() {
  if ('serviceWorker' in navigator) {
    navigator.serviceWorker.ready
      .then(registration => {
        registration.unregister();
      })
      .catch(error => {
        console.error(error.message);
      });
  }
}
```

В этом примере мы определяем функции `register()` и `unregister()`, которые используются для регистрации и отмены регистрации Service Worker. Обратите внимание, что эти функции используются в `index.js` для регистрации Service Worker и в других частях приложения для управления Service Worker.

Код модуля `serviceWorker.js` проверяет, поддерживает ли браузер Service Worker, и если да, то регистрирует Service Worker. Также в этом модуле определены функции для проверки наличия обновлений и обработки событий обновления Service Worker. В целом, это общий шаблон для инициализации Service Worker в приложении React.

## Заключение

В заключение, `registerServiceWorker()` - это функция из библиотеки React, которая позволяет зарегистрировать Service Worker в приложении. Service Worker предоставляет множество преимуществ, таких как улучшенная производительность, офлайн-доступ, локальное хранение данных и push-уведомления.

Однако, Service Worker также имеет некоторые ограничения, такие как ограничения безопасности, ограничения кэширования и ограничения на доступность API, которые нужно учитывать при использовании этой технологии.

Для инициализации `registerServiceWorker()` в приложении React, необходимо импортировать функцию `register()` из модуля `serviceWorker.js` и вызвать ее после рендеринга нашего приложения. Модуль `serviceWorker.js` определяет функции для регистрации, проверки наличия обновлений и обработки событий Service Worker.

В целом, использование Service Worker может значительно улучшить функциональность, производительность и безопасность вашего приложения, и `registerServiceWorker()` является важной функцией для инициализации Service Worker в приложении React.