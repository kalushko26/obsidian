---
title: С какой версии React пользуешься и какие крупные изменения за это время произошли?
draft: false
tags:
  - "#React"
  - "#useContext"
  - "#useReducer"
  - fiber
  - concurrentMode
  - Hooks
info:
  - https://habr.com/ru/companies/yandex/articles/514016/
---
Версия React, которая была актуальной в 2019 году, - это версия 16.8.0, которая была выпущена в феврале 2019 года. В этой версии был представлен новый хук `useContext()`, который позволяет компонентам получать доступ к контексту приложения без необходимости передавать пропсы через дерево компонентов. Также был представлен новый хук `useReducer()`, который предоставляет более мощный способ управления состоянием компонента.

В более поздних версиях React были внесены другие крупные изменения. Например, в версии 16.9.0 был представлен новый хук `useDebugValue()`, который позволяет добавлять дополнительную информацию для отладки пользовательских хуков. В версии 16.13.0 были введены новые функции `React.memo()` и `React.lazy()`, которые улучшают производительность и оптимизацию загрузки компонентов.

С версии 17.0.0 React перешел на новую модель рендеринга, которая называется React Concurrent Mode. Эта модель позволяет React более эффективно использовать ресурсы процессора и сети, улучшая отзывчивость приложений и уменьшая время ожидания для пользователей.

Также стоит отметить, что в более поздних версиях React были внесены изменения, которые упрощают работу с хуками, улучшают типизацию и улучшают производительность. В целом, React продолжает развиваться и улучшаться, внедряя новые функции и инструменты, которые помогают разработчикам создавать более эффективные и масштабируемые приложения.

---

[[004 ReactCore|Назад]]