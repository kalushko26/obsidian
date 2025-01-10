---
title: Union и TypeGuards, пользовательские проверки типов
draft: false
tags:
  - "#TypeScript"
  - "#union"
  - "#TypeGuard"
info:
  - https://www.youtube.com/watch?v=P2Ny05sAYoY
  - https://www.youtube.com/watch?v=bO1R4SnE8r8
---
`TypeGuard (охранник типа)` - это механизм, который позволяет проверять типы значений во время выполнения программы и обеспечивает безопасность типов в TypeScript.

`TypeGuard` позволяет определять функции, которые могут проверять типы значений и возвращать булевое значение, указывающее, соответствует ли значение определенному типу. Если функция возвращает `true`, TypeScript рассматривает значение как соответствующее этому типу, и в дальнейшем можно использовать свойства и методы этого типа без ошибок компиляции.

Например, рассмотрим следующий код:

```typescript
function isString(value: any): value is string {
  return typeof value === "string";
}

let value: any = "hello";

if (isString(value)) {
  console.log(value.toUpperCase()); // Вывод: HELLO
} else {
  console.log("Value is not a string");
}
```

Здесь мы определяем функцию `isString`, которая проверяет, является ли значение типом `string`. Затем мы используем `isString` в условном операторе для проверки типа значения переменной `value`. Если `isString` возвращает `true`, мы можем безопасно использовать метод `toUpperCase` для строки `value`, так как TypeScript теперь рассматривает `value` как тип `string`.

_____

[[005 TypeScript|Назад]]