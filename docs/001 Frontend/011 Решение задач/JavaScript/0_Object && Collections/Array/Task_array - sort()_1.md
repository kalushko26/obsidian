---
title: Task_array - sort()_1
draft: false
tags:
  - "#JavaScript"
  - "#taskJS"
  - "#array"
  - "#sort"
  - "#unknownINC"
---
```
// Есть задача функция принимает массив чисел, 
// необхоимо вернуть массив с наибольшими числами в порядке убывания, 
// например принимает[1, 2, 5, 3, 4, 6, 4,] - вернуть[6, 5]
```

**Ответ

```js
const array = [1, 2, 5, 3, 4, 6, 4,];

function sorted(array) {
  return array.sort((a, b) => b - a)
}

console.log(sorted(array))
```

___

[[011 Решение задач JS, TS и React|Назад]]