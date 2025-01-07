---
title: Что такое композиция в контексте JavaScript?
draft: false
tags:
  - ООП
  - class
  - композиция
info:
---
![[Pasted image 20230703184222.png|600]]

*`Композиция`* - это паттерн проектирования, который *позволяет создавать более сложные объекты из простых компонентов.* В контексте JavaScript *композиция - это способ создания объектов, которые состоят из других объектов, используя их функциональность для создания более сложных объектов.* Этот подход позволяет создавать более гибкие и модульные программы, в которых объекты могут быть переиспользованы в разных контекстах.

В JavaScript композиция может быть реализована *с помощью функций, которые возвращают новые объекты, состоящие из других объектов.* Эти функции могут использовать свойства и методы других объектов, чтобы создать новые объекты с нужной функциональностью.

Вот пример реализации композиции в JavaScript:

```js
function createPerson(name) {
  const state = {
    name: name,
    age: null,
    gender: null,
  };

  function setAge(age) {
    state.age = age;
  }

  function setGender(gender) {
    state.gender = gender;
  }

  function getState() {
    return state;
  }

  return {
    setAge,
    setGender,
    getState,
  };
}

function createEmployee(name, position) {
  const person = createPerson(name);
  const state = {
    position: position
  };

  function setPosition(position) {
    state.position = position;
  }

  function getState() {
    return {
      ...person.getState(),
      ...state
    };
  }

  return {
    ...person,
    setPosition,
    getState,
  };
}

const employee = createEmployee('John', 'Manager');
employee.setAge(30);
employee.setGender('Male');
employee.setPosition('Senior Manager');
console.log(employee.getState());
```

В этом примере мы создаем функцию `createPerson`, которая возвращает объект с методами `setAge`, `setGender` и `getState`. Затем мы создаем функцию `createEmployee`, которая создает объект с помощью функции `createPerson` и добавляет к нему метод `setPosition`. Мы также переопределяем метод `getState`, чтобы он возвращал объект, содержащий свойства из объекта `person` и объекта `state`.

___

[[200 Браузерное окружение|Назад]]