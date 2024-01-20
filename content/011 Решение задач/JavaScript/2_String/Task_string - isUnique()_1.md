tags: #JavaScript #taskJS #string 
____

```js
function isUnique(string) {
	// todo
}

console.log(isUnique('abcdef')) // -> true
console.log(isUnique('1234567')) // -> true
console.log(isUnique('abcABC')) // -> true
console.log(isUnique('abcadef')) // -> false
```

### Ответ

```js
function isUnique(str) {
    return [...new Set(str)].join('') === str;
}
```

___
### [[011 Решение задач JS, TS и React|Назад]]