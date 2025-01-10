---
title: Какова цель использования constructor (super) с аргументом props?
draft: false
tags:
  - "#React"
  - "#constructor"
  - "#super"
  - "#props"
info:
---
Конструктор дочернего класса не может использовать ссылку `this` до тех пор, пока не будет вызван метод `super()`. То же самое относится и к подклассам ES6. Основная причина передачи параметра props вызову `super()` заключается в доступе к `this.props` в ваших дочерних конструкторах.

**Пропуская props:**

```js
class MyComponent extends React.Component {
  constructor(props) {
    super(props)

    console.log(this.props) // prints { name: 'John', age: 42 }
  }
}
```

**Не пропуская props:**

```js
class MyComponent extends React.Component {
  constructor(props) {
    super()

    console.log(this.props) // prints undefined

    // но параметр props по-прежнему доступен
    console.log(props) // prints { name: 'John', age: 42 }
  }

  render() {
    // никакой разницы вне конструктора
    console.log(this.props) // prints { name: 'John', age: 42 }
  }
}
```

Приведенные выше фрагменты кода показывают, что `this.props` отличается только внутри конструктора. Это было бы то же самое вне конструктора.

---

[[004 ReactCore|Назад]]