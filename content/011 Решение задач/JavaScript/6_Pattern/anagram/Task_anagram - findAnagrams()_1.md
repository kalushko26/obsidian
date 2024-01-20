tags: #JavaScript #taskJS #anagram 
____

```js
/*
Описание:
Напишите функцию, которая принимает массив слов 
и возвращает массив, содержащий все пары слов, 
являющиеся анаграммами.

// console.log(findAnagrams(["listen", "silent", "hello", "loleh", "cat", "act", "pips"]));
// ["listen", "silent", "hello", "loleh", "cat", "act"]
*/
```

### Ответ

```js
function findAnagrams(wordArr) {
  let anagramObj = {};

  for (let word of wordArr) {
    const sorted = word.split("").sort().join("");

    if (anagramObj[sorted]) {
      anagramObj[sorted].push(word);
    } else {
      anagramObj[sorted] = [word];
    }
  }

  const filtered = Object.values(anagramObj).filter((arr) => arr.length > 1);

  return filtered.flat(Infinity);
}
```

___
### [[011 Решение задач JS, TS и React|Назад]]
