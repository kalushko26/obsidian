---
title: Разница между `React` и `ReactDOM`
draft: false
tags:
  - "#React"
  - "#ReactDOM"
  - DOM
  - "#render"
  - "#JSX"
  - "#XSS"
info:
  - https://ittutoria.net/reactdom-render-is-no-longer-supported-in-react-18-use-createroot-instead/
---
![[Pasted image 20230704173402.png|600]]

`React` и `ReactDOM` - это две разные библиотеки, которые используются в React-приложениях. Но обычно импортируются обе библиотеки, чтобы использовать их функциональности вместе.

**React** - _это библиотека JavaScript для создания пользовательских интерфейсов._

**ReactDOM** - это библиотека, которая предоставляет интеграцию `React` с DOM. *Она используется для рендеринга `React` компонентов в реальный DOM.* `ReactDOM` содержит методы для манипулирования реальным DOM, такие как `ReactDOM.render()`, который используется для рендеринга React-компонентов в DOM.

_По умолчанию React DOM [экранирует](https://stackoverflow.com/questions/7381974/which-characters-need-to-be-escaped-on-html) все значения, включённые в JSX перед тем как отрендерить их._ Это гарантирует, что вы никогда не внедрите чего-либо, что не было явно написано в вашем приложении. Всё преобразуется в строчки, перед тем как быть отрендеренным. Это помогает предотвращать атаки [межсайтовым скриптингом (XSS)](https://ru.wikipedia.org/wiki/%D0%9C%D0%B5%D0%B6%D1%81%D0%B0%D0%B9%D1%82%D0%BE%D0%B2%D1%8B%D0%B9_%D1%81%D0%BA%D1%80%D0%B8%D0%BF%D1%82%D0%B8%D0%BD%D0%B3) .

**Устранение ошибки:** “ReactDOM.render больше не поддерживается в React 18. Вместо этого используйте createRoot”

---

[[004 ReactCore|Назад]]