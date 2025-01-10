---
title: TSTask - MyType()_1
draft: false
tags:
  - "#TypeScript"
  - "#tsTask"
  - "#types"
  - "#детскийМир"
---
```ts
type MyType = any;

const values: MyType[] = [{
	type: 'number',
	value: 42,
}, {
	type: 'string',
	message: 'Hello, World!'
}, {
	type: 'range',
	from: 0,
	to: 100,
}];

console.log(values);
```

**Ответ

```ts
type MyType = {
  type: string,
  value?: number,
  message?: string,
  from?: number,
  to?: number
};

const values: MyType[] = [{
    type: 'number',
    value: 42,
}, {
    type: 'string',
    message: 'Hello, World!'
}, {
    type: 'range',
    from: 0,
    to: 100,
}];

console.log(values);
```

___

[[011 Решение задач JS, TS и React|Назад]]