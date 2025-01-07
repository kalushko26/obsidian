---
title: TSTask - getProperty()_0
draft: false
tags:
  - TypeScript
  - tsTask
---
```ts
// Исправь код
const X = { a: 1, b: 2, c: 3, d: 4 } 

function getProperty(obj, key){ 
	return obj[key] 
} 

getProperty(X, 'a') getProperty(X, 'm') // Error
```

**Ответ

```ts
const X = { a: 1, b: 2, c: 3, d: 4 } 

function getProperty<T, K extends keyof T>(obj:T, key:K): T[K]{ 
	return obj[key] 
}
```

// НЕМНОГО НЕ ПОЙМУ, ЧТО ЗДЕСЬ НАДО БЫЛО ДЕЛАТЬ


___

[[011 Решение задач JS, TS и React|Назад]]