---
title: Task_anagram - anagram(str)_1
draft: false
tags:
  - "#JavaScript"
  - "#taskJS"
  - "#anagram"
  - "#промсвязьбанк"
---
```js
// Принять массив строк, вернуть массив массивов анаграмм: 
// ["тьма", "мать", "адрес", "среда", "поток"] → [["тьма", "мать"], ["адрес", "среда"]] 

function anagram(str) {
	// Ваш код здесь
}
```

**Ответ

```js
function anagram(str) {
  let ang = {}
  
  for (let word of str) {
    const sorted = word.split('').sort().join('')
    if(ang[sorted]){
      ang[sorted].push(word)
    }else{
      ang[sorted] = [word]
    }
  }
  return Object.values(ang).filter(el => el.length > 1)
}
```

___

[[011 Решение задач JS, TS и React|Назад]]