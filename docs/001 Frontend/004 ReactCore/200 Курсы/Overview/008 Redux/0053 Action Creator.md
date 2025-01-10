---
title: Action Creator
draft: false
tags:
  - React
  - "#Redux"
  - "#action"
---
`Actiom Creator` - функция, которая создаёт объекты `action` .

Упрощает код:

```jsx
const userLoggedIn = ( name, role ) => {
	return {type: 'USER_LOGGED_IN', name, role};
}

store.dispatch(userLoggedIn('Arnold', 'admin'))
```

_____
