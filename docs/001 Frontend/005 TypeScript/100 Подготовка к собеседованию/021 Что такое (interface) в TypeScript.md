---
title: Что такое (`interface`) в TypeScript?
draft: false
tags:
  - "#TypeScript"
  - "#interface"
info:
---
`interface` определяет свойства и методы, которые объект должен реализовать. Другими словами, интерфейс - это определение кастомного типа данных, но без реализации.

```typescript
interface IEmployee {
	empCode: number;
	empName: string;
	getSalary: (number) => number; // arrow function
	getManagerName(number): string;
}
```

_____

[[005 TypeScript|Назад]]