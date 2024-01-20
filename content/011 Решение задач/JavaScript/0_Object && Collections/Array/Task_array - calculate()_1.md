#JavaScript #array #taskJS 
____

```js
function calculate(arr) {
// Ваш код здесь
} 

console.log(calculate([5, 0, -5, 20, 88, 17, -32])) // 22
```

### Ответ

```js
function calculate(arr) {
	let newArr = []
	for(let i = 0; i < arr.length; i++) {
		if(arr[i]%2 !== 0 && arr[i] > 0) {
		newArr.push(arr[i])
		}
	}
	return newArr.reduce((acc, el) => {
		return acc = acc + el;
	}, 0)
}

console.log(calculate([5, 0, -5, 20, 88, 17, -32])) // 22
```

___
### [[011 Решение задач JS, TS и React|Назад]]