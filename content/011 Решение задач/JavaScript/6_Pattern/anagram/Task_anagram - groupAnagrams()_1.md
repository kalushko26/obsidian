tags: #JavaScript #taskJS #anagram 
____

```js
/*
Описание: 
Напишите функцию, которая принимает массив слов и 
возвращает массив, содержащий все анаграммы группированные в подмассивы.

groupAnagrams(["listen", "silent", "hello", "loleh", "cat", "act"]);
// [["listen", "silent"], ["hello", "loleh"], ["cat", "act"]]
*/
```

### Ответ

```js
function groupAnagrams(arr) {
  let grAnagram = {};

  for (let anagram of arr) {
    const sorted = anagram.split("").sort().join("");
    if (grAnagram[sorted]) {
      grAnagram[sorted].push(anagram);
    } else {
      grAnagram[sorted] = [anagram];
    }
  }

  return Object.values(grAnagram);
}
```

___
### [[011 Решение задач JS, TS и React|Назад]]