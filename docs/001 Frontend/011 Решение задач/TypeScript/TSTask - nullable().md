---
title: TSTask - nullable()
draft: false
tags:
  - "#TypeScript"
  - "#tsTask"
  - "#nonnullable"
  - "#unknownINC"
---
```ts
const obj = {
	a: string,
	b: number
}

const nullableObj = {
	a: string | null,
	b: number | null
}
```

**Ответ

```ts
type Nullable<T> = {  
    [P in keyof T]: T[P] | null;
};
```

____

[[011 Решение задач JS, TS и React|Назад]]