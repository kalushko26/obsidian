---
title: Как передавать пропсы в React Router?
draft: false
tags:
  - "#React"
  - "#React-router"
  - "#props"
info:
---
![[Pasted image 20230704215258.png|600]]

В React Router можно передавать пропсы через _компоненты маршрутизации_.

Пропсы могут быть переданы двумя способами: через атрибуты `component` и `render`.

1. Атрибут `component`:

```jsx
import { Route } from "react-router-dom"

function MyComponent(props) {
  return <div>{props.text}</div>
}

function App() {
  return <Route path="/my-route" component={() => <MyComponent text="Hello, World!" />} />
}
```

2. Атрибут `render`:

```jsx
import { Route } from "react-router-dom"

function MyComponent(props) {
  return <div>{props.text}</div>
}

function App() {
  return <Route path="/my-route" render={() => <MyComponent text="Hello, World!" />} />
}
```

В обоих случаях мы создаем маршрут для пути "/my-route" и рендерим компонент `MyComponent`. Пропс `text` передается в компонент через атрибуты `component` или `render`.

Если вы хотите передать дополнительные пропсы в компонент, вы можете использовать метод расширения объекта:

```jsx
import { Route } from "react-router-dom"

function MyComponent(props) {
  return (
    <div>
      <p>{props.text}</p>
      <p>{props.anotherProp}</p>
    </div>
  )
}

function App() {
  return (
    <Route
      path="/my-route"
      render={(routeProps) => (
        <MyComponent text="Hello, World!" anotherProp="Another prop value" {...routeProps} />
      )}
    />
  )
}
```

В этом примере мы добавляем проп `anotherProp` в компонент `MyComponent`, а также передаем все пропсы маршрутизации через метод расширения объекта (`...routeProps`).

---

[[004 ReactCore|Назад]]