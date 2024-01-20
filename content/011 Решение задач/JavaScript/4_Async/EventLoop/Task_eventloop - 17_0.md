tags: #JavaScript #taskJS #EventLoop #астон
____

```js
setTimeout(() => console.log('a'));

Promise.resolve()
	.then((first) => {
	console.log('first:', first)
	return 'b'
	})
	.then(
		Promise.resolve().then((second) => {
		console.log('second:', second);
		return 'c';
		})
		)
		.then((third) => console.log('third:', third));

console.log('d')

// d
// first: 1. undefined
// second:1. undefined
// third: b
// a
```


___
### [[011 Решение задач JS, TS и React|Назад]]