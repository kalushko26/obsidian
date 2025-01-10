---
title: Что делает тип Omit?
draft: false
tags:
  - "#TypeScript"
  - "#omit"
info:
---
`Omit` - это форма служебного типа, которая упрощает преобразования общих типов. `Omit` *позволяет вам создать тип, передав текущий тип и выбрав ключи, которые нужно пропустить в новом типе.*

```typescript
Omit<Type, Keys>;
```

Например:

```typescript
interface Todo {
	title: string;
	description: string;
	completed: boolean;
	createdAt: number;
}

type TodoPreview = Omit<Todo, "description">;
```

_____

[[005 TypeScript|Назад]]