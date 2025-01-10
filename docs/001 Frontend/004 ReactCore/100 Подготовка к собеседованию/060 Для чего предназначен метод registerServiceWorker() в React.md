---
title: Для чего предназначен метод `registerServiceWorker()` в React?
draft: false
tags:
  - "#React"
  - "#registerServiceWorker"
  - "#serviceWorker"
  - "#navigator"
info:
  - "[[registerServiceWorker()]]"
  - https://habr.com/ru/companies/2gis/articles/345552/
---
*`registerServiceWorker()`* - это метод, который можно использовать в React-приложении для регистрации Service Worker'а.

_Service Worker_ - это скрипт, который работает в фоновом режиме и позволяет кэшировать ресурсы, такие как HTML-файлы, стили, скрипты и изображения. Это позволяет улучшить производительность приложения, уменьшить время загрузки и улучшить пользовательский опыт.

_Метод `registerServiceWorker()` используется для регистрации Service Worker'а в браузере. Он проверяет, поддерживает ли браузер Service Worker, и если да, то регистрирует его. После регистрации Service Worker начинает работать в фоновом режиме и кэшировать ресурсы._

Пример использования метода `registerServiceWorker()`:

```jsx
import React from "react"
import ReactDOM from "react-dom"

ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById("root"),
)

// Регистрация Service Worker'а
if ("serviceWorker" in navigator) {
  window.addEventListener("load", () => {
    navigator.serviceWorker
      .register("/sw.js")
      .then((registration) => {
        console.log("ServiceWorker registered: ", registration)
      })
      .catch((registrationError) => {
        console.log("ServiceWorker registration failed: ", registrationError)
      })
  })
}
```

В данном примере мы регистрируем Service Worker в браузере при помощи метода `register()` из объекта `navigator.serviceWorker`. Если регистрация прошла успешно, то в консоли будет выведено сообщение "ServiceWorker registered". Если регистрация не удалась, то будет выведено сообщение "ServiceWorker registration failed".

---

[[004 ReactCore|Назад]]