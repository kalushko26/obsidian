tags: #JavaScript #taskJS #anagram 
____

```js
/*
Описание: 
Напишите функцию, которая принимает предложение и 
возвращает массив всех анаграмм слов в предложении. 
Игнорируйте знаки препинания и регистр букв.

findAnagramWords("Listen silent, I am listen!"); 
*/
```

### Ответ

```js
function findAnagramWords(str) {
  const findedAnag = {};
  const regExp = /[^\w|\s]/gm;
  const replaced = str.replace(regExp, "").split(" ");

  for (let anagram of replaced) {
    const sorted = anagram.toLowerCase().split("").sort().join("");
    if (findedAnag[sorted]) {
      findedAnag[sorted].push(anagram);
    } else {
      findedAnag[sorted] = [anagram];
    }
  }
  return Object.values(findedAnag).filter((el) => el.length > 1);
}
```

___
### [[011 Решение задач JS, TS и React|Назад]]