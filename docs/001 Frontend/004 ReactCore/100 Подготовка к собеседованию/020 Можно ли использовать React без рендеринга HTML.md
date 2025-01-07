---
title: Можно ли использовать React без рендеринга HTML?
draft: false
tags:
  - "#React"
  - "#render"
info:
---
Это возможно. Ниже приведены возможные варианты:

```js
render() {
  return false
}
```

```js
render() {
  return true
}
```

```js
render() {
  return null
}
```

React version >=16.0.0:

```js
render() {
  return []
}
```

```js
render() {
  return ""
}
```

React version >=16.2.0:

```js
render() {
  return <React.Fragment></React.Fragment>
}
```

```js
render() {
  return <></>
}
```

React version >=18.0.0:

```js
render() {
  return undefined
}
```

---

[[004 ReactCore|Назад]]