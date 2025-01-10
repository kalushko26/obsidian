---
title: Объясните назначение свойства `headers` в next.config.js
draft: false
tags:
  - NextJS
  - next-config
  - header
info:
  - https://nextjs.org/docs/pages/api-reference/next-config-js/headers
---
Свойство `headers` в файле `next.config.js` используется для определения пользовательских HTTP-заголовков, которые должны быть включены в ответы, обслуживаемые вашим приложением Next.js. Это свойство позволяет разработчикам устанавливать различные HTTP-заголовки, такие как политики кэширования, заголовки, связанные с безопасностью, и другие пользовательские заголовки, для управления взаимодействием браузеров и клиентов с приложением.

Вот пример того, как можно использовать свойство `headers`:

```javascript
// next.config.js
module.exports = {
  async headers() {
    return [
      {
        source: '/path/:slug', // может быть конкретным путем или шаблоном
        headers: [
          {
            key: 'Custom-Header',
            value: 'Custom-Header-Value',
          },
          {
            key: 'Cache-Control',
            value: 'public, max-age=3600', // установка политики кэширования
          },
          // Добавьте другие заголовки по мере необходимости
        ],
      },
    ]
  },
  // другие конфигурации...
}
```

____

[[006 Next.js|Назад]]