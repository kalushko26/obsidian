tags: #JavaScript #flat #taskJS 
____

```js
function flatten(array) {
// Ваш код здесь
}

console.log(flatten([[1], [[2, 3]], [[[[[4]]]]]])); // -> [1, 2, 3, 4]
```

### Ответ

```js
const arr = [[1], [[2, 3]], [[[4]]]]

function flatten(arr) {
	return arr.flat(Infinity)
}

console.log(flatten(arr)); // -> [1, 2, 3, 4]
```

```js
function flatten(array) {
  let newArr = [];

  for(let name of array) {
      if(Array.isArray(name)) {
         newArr = newArr.concat(flatten(name))
      } else {
          newArr.push(name)
      }
  }
  return newArr
}

console.log(flatten([[1], [[2, 3]], [[[[[4]]]]]])); // -> [1, 2, 3, 4]

```

___
### [[011 Решение задач JS, TS и React|Назад]]