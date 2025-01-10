---
title: Можно ли в JavaScript реализовать абстрактный класс и как это сделать?
draft: false
tags:
  - ООП
  - class
  - абстракция
info:
---
В JavaScript есть несколько способов реализации *абстрактных классов*. Один из таких способов - использование *функций-конструкторов и прототипов*.

Вот пример реализации абстрактного класса в JavaScript:

```js
function AbstractClass() {
  if (this.constructor === AbstractClass) {
    throw new Error("Cannot instantiate abstract class");
  }
}

AbstractClass.prototype.abstractMethod = function() {
  throw new Error("Method 'abstractMethod' must be implemented");
};
```

В этом примере мы создаем функцию-конструктор `AbstractClass`, которая бросает исключение при попытке создания экземпляра абстрактного класса. Затем мы добавляем метод `abstractMethod` в прототип `AbstractClass`, который бросает исключение при вызове, если метод не был переопределен в наследующем классе.

Чтобы создать класс, наследующий от абстрактного класса, мы можем использовать следующий код:

```js
function ConcreteClass() {
  AbstractClass.call(this);
}

ConcreteClass.prototype = Object.create(AbstractClass.prototype);
ConcreteClass.prototype.constructor = ConcreteClass;

ConcreteClass.prototype.abstractMethod = function() {
  // implementation
};
```

В этом примере мы создаем функцию-конструктор `ConcreteClass`, которая вызывает функцию-конструктор `AbstractClass` с помощью метода `call` и устанавливает прототип `ConcreteClass` равным прототипу `AbstractClass`. Затем мы переопределяем метод `abstractMethod` в прототипе `ConcreteClass` с конкретной реализацией.

Таким образом, используя функции-конструкторы и прототипы, можно реализовать абстрактные классы в JavaScript. Однако, важно помнить, что это не является настоящим абстрактным классом, так как JavaScript не имеет встроенной поддержки для этого. Вместо этого мы используем соглашения и паттерны для достижения того же эффекта.

___

[[200 Браузерное окружение|Назад]]