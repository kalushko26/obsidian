tags: #JavaScript #taskJS #string #RegExp #newsMediaINC
___

```js
/**
 * Функция должна преобразовывать строку в формат camelCase
 * @param str {string}
 */

const str = "mY-comPonent name";

function camelCase(str) {
 // Ваш код здесь
}

console.log(camelCase("mY-comPonent name") === "MyComponentName");
console.log(camelCase(str))
```

### Ответ

```js
const str = "mY-comPonent name";

function camelCase(str) {
  const reg = /[^a-zA-Z]/gm
  const strArr = str.replace(reg, ' ').toLowerCase().split(' ');
  let arr = [];

  for (let i = 0; i < strArr.length; i++) {
    arr.push(strArr[i].charAt(0).toUpperCase() + strArr[i].slice(1))
  }
  return arr.join('')
}

console.log(camelCase("mY-comPonent name") === "MyComponentName");
console.log(camelCase(str))
```

___
### [[011 Решение задач JS, TS и React|Назад]]