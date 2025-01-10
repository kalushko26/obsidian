---
title: ReactTask - ControlledComponent_0
draft: false
tags:
  - "#React"
  - "#reactTask"
  - "#unknownINC"
  - "#controlled"
---
```js
// Вывести значения первого и второго инпута учитываю что один конролируемый а второй нет

function F() {
  const fn = () => {
    console.log("first input value : ");
    console.log("second input value : ");
  };
  return (
    <form onClick={fn}>
      <input placeholder="controlled field"></input>
      <input placeholder="uncontrolled field"></input>
      <button>Отправить</button>
    </form>
  );
}
```

___

[[011 Решение задач JS, TS и React|Назад]]