tags: #JavaScript #taskJS #anagram 
____

```js
/*
Описание: Напишите функцию, которая принимает две строки 
и определяет, являются ли они анаграммами 
(имеют одинаковые буквы в разном порядке).
Пример:
// console.log(isAnagram("listen", "silent")); // true
// console.log(isAnagram("hello", "world")); // false
*/
```

### Ответ

```js
function isAnagram(str1, str2) {
  return true
    ? str1.split("").sort().join("") === str2.split("").sort().join("")
    : false;
}
```

___
### [[011 Решение задач JS, TS и React|Назад]]
