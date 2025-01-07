---
title: Опишите, как в React обрабатываются события?
draft: false
tags:
  - "#React"
  - "#SyntheticEvent"
  - "#event"
info:
---
В React обработка событий происходит с помощью _передачи функций-обработчиков в качестве атрибутов JSX элементов._ Когда происходит событие, React вызывает соответствующую функцию-обработчик и передает ей объект `event`.

Например, чтобы обработать клик на кнопке, мы можем передать функцию-обработчик в атрибут `onClick`:

```jsx
class MyComponent extends React.Component {
  handleClick(event) {
    console.log("Button clicked!")
  }

  render() {
    return <button onClick={this.handleClick}>Click me</button>
  }
}
```

В этом примере мы определяем метод `handleClick()`, который вызывается при клике на кнопку. Мы передаем этот метод в атрибут `onClick` элемента `button`. Когда пользователь кликает на кнопке, React вызывает метод `handleClick()` и передает ему объект `event`.

Кроме того, в React есть несколько специальных событий, которые можно использовать для определенных действий, например: *`onSubmit` для обработки отправки формы, `onChange` для обработки изменения значения элемента формы и т.д.*

```jsx
class MyForm extends React.Component {
  handleSubmit(event) {
    event.preventDefault()
    console.log("Form submitted!")
  }

  handleInputChange(event) {
    console.log(`Input value: ${event.target.value}`)
  }

  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <label>
          Name:
          <input type="text" onChange={this.handleInputChange} />
        </label>
        <button type="submit">Submit</button>
      </form>
    )
  }
}
```

В этом примере мы определяем два метода: `handleSubmit()` для обработки отправки формы и `handleInputChange()` для обработки изменения значения элемента формы. Мы передаем эти методы в атрибуты `onSubmit` и `onChange` соответственно. Когда пользователь отправляет форму, React вызывает метод `handleSubmit()`, который отменяет стандартное поведение (перезагрузку страницы) с помощью метода `preventDefault()`. Когда пользователь изменяет значение текстового поля, React вызывает метод `handleInputChange()` и передает ему объект `event`.

---

[[004 ReactCore|Назад]]