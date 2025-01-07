---
title: В чем разница между super() и super(props) в React с использованием классов ES6?
draft: false
tags:
  - "#React"
  - "#constructor"
  - "#super"
  - "#props"
info:
---
Если вы хотите получить доступ к `this.props` в `constructor()`, тогда вы должны передать props методу `super()`.

**Использование  `super(props)`:**

```js
class MyComponent extends React.Component {
  constructor(props) {
    super(props)
    console.log(this.props) // { name: 'John', ... }
  }
}
```

**Использование `super()`:**

```js
class MyComponent extends React.Component {
  constructor(props) {
    super()
    console.log(this.props) // undefined
  }
}
```

Вне `constructor()` оба будут отображать одинаковое значение для `this.props`.

---

[[004 ReactCore|Назад]]