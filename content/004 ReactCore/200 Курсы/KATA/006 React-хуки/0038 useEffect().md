____

tags: #React #Hooks #useEffect

Запускает функцию каждый раз , когда определенный набор данных изменяется .

```jsx
useEffect (() => {
	console.log(a + b + c);
	return () => console.log('cleanup')
}, [a , b, c]);
```

Если вернуть функцию , она будет вызываться для очистки предыдущего эффекта (похоже на componentWillUnmount())

_____

