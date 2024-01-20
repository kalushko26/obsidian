tags: #JavaScript #taskJS #anagram 
____

```js
/*
Описание:
Напишите функцию, которая принимает массив слов и
возвращает самую длинную цепочку анаграмм в виде массива.

Пример:
findLongestAnagramChain(["listen", "silent", "hello", "loleh", "cat", "act"]);
// ["listen", "silent"]
*/
```

### Ответ

```js
function findLongestAnagramChain(arr) {
  const grpAnagrams = {};

  for (let name of arr) {
    const sorted = name.split("").sort().join("");
    if (grpAnagrams[sorted]) {
      grpAnagrams[sorted].push(name);
    } else {
      grpAnagrams[sorted] = [name];
    }
  }

  let maxChain = [];
  for (let word of Object.values(grpAnagrams)) {
    const chain = word.join("").length;
    if (chain > maxChain) {
      maxChain = word;
    }
  }

  return maxChain;
}
```

___
### [[011 Решение задач JS, TS и React|Назад]]