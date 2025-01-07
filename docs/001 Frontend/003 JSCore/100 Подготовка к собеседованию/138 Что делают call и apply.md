---
title: Что делают call и apply?
draft: false
tags:
  - "#JavaScript"
  - "#bind"
  - "#call"
  - "#apply"
info:
  - "[[0057 Декораторы и переадресация вызова, сall и apply|Методы call & apply]]"
---
![[Pasted image 20230703114905.png|600]]

Методы `call`, `apply` и `bind` являются методами функции в JavaScript и позволяют управлять контекстом выполнения функции, т.е. значением `this`.

*Метод `call`* позволяет _вызывать функцию с явно заданным контекстом выполнения и передавать аргументы в виде отдельных значений_. Первый аргумент метода `call` устанавливает значение `this`, а последующие аргументы передаются в вызываемую функцию. Например:

```javascript
const person = {
  firstName: "John",
  lastName: "Doe",
  getFullName: function () {
    return this.firstName + " " + this.lastName
  },
}

const person2 = {
  firstName: "Jane",
  lastName: "Doe",
}

console.log(person.getFullName.call(person2)) // 'Jane Doe'
```

*Метод `apply`* работает *аналогично методу* `call`, но _принимает аргументы в виде массива._ Первый аргумент метода `apply` устанавливает значение `this`, а второй аргумент должен быть массивом аргументов, которые будут переданы в вызываемую функцию. Например:

```javascript
const numbers = [1, 2, 3, 4, 5]

const sum = function () {
  return this.reduce(function (acc, val) {
    return acc + val
  }, 0)
}

console.log(sum.apply(numbers)) // 15
```

*Метод `bind`* позволяет _создать новую функцию с жестко привязанным контекстом выполнения (значением `this`)_. Метод `bind()` возвращает новую функцию с привязанным контекстом. Эта новая функция может быть вызвана позже с любым количеством аргументов. Например:

```javascript
const person = {
  firstName: "John",
  lastName: "Doe",
  getFullName: function () {
    return this.firstName + " " + this.lastName
  },
}

const logFullName = function () {
  console.log(this.getFullName())
}

const boundLogFullName = logFullName.bind(person)

boundLogFullName() // 'John Doe'
```

Основное отличие между `call` и `apply` заключается в том, как аргументы передаются в вызываемую функцию (в виде отдельных значений или массива соответственно), а `bind` создает новую функцию с жестко привязанным контекстом, которая может быть вызвана позже. При использовании этих методов важно помнить, что `call` и `apply` вызывают функцию немедленно, в то время как `bind` создает новую функцию, которая может быть вызвана позже.

---

[[003 JSCore|Назад]]