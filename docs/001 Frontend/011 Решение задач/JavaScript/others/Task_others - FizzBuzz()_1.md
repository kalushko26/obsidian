---
title: Task_others - FizzBuzz()_1
draft: false
tags:
  - "#JavaScript"
  - "#taskJS"
  - "#switchCase"
  - "#SignalINC"
---
```js
// FizzBuzz - написать функцию которая в качестве аргумента принимает целое, 
// положительное число n, результатом работы функции должен быть массив строк длиной n элементов в котором:

function fizzBuzz(number) {
 // Ваш код здесь
}

console.log(fizzBuzz(15), `Делится на 3 и 5`);
console.log(fizzBuzz(12), `Делится на 3`);
console.log(fizzBuzz(20), `Делится на 5`);
console.log((fizzBuzz(number)), `не удовлетворяется ни одно из условий`);
```

### Ответ

```js
let number = 2;

function fizzBuzz(number) {
  let result = [];

  switch (true) {
    case number % 3 === 0 && number % 5 === 0:
      result.push("FizzBuzz");
      break;
    case number % 3 === 0 && number % 5 !== 0:
      result.push("Fizz");
      break;
    case number % 5 === 0 && number % 3 !== 0:
      result.push("Buzz");
      break;
    default:
      result.push(number.toString());
  }
  return result;
}

console.log(fizzBuzz(15), `Делится на 3 и 5`);
console.log(fizzBuzz(12), `Делится на 3`);
console.log(fizzBuzz(20), `Делится на 5`);
console.log((fizzBuzz(number)), `не удовлетворяется ни одно из условий`);
```

___

[[011 Решение задач JS, TS и React|Назад]]