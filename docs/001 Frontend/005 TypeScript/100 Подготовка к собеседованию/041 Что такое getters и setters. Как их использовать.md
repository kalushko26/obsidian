---
title: Что такое getters и setters. Как их использовать?
draft: false
tags:
  - "#TypeScript"
  - "#getters"
  - "#setters"
info:
---
Геттеры и сеттеры - это особые типы методов, которые помогают делегировать различные уровни доступа к частным переменным в зависимости от потребностей программы.

**Геттеры** позволяют ссылаться на значение, но не могут его редактировать. 
**Сеттеры** позволяют изменять значение переменной, но не видеть ее текущее значение. 
*Это важно для достижения инкапсуляции.*

Например, новый работодатель может получить количество сотрудников в компании, но не имеет разрешения устанавливать количество сотрудников.

```typescript
const fullNameMaxLength = 10;

class Employee {
	private _fullName: string = "";

	get fullName(): string {
		return this._fullName;
	}

	set fullName(newName: string) {
		if (newName && newName.length > fullNameMaxLength) {
			throw new Error("fullName has a max length of " + fullNameMaxLength);
		}

		this._fullName = newName;
	}
}

let employee = new Employee();
employee.fullName = "Bob Smith";

if (employee.fullName) {
	console.log(employee.fullName);
}
```

_____

[[005 TypeScript|Назад]]