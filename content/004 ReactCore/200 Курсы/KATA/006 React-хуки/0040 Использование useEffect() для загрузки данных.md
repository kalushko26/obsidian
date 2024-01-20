____

tags: #React #Hooks #useEffect 

Если данные зависят от параметра (например, ID ресурса) - обязательно укажите его в массиве > Promise нельзя отменить, но можно проигнорировать результат:

```jsx
useEffect(() => {
let cancelled = false;
fetch(`/users/${id}`)
	.then(res => res.json())
	.then(data => !cancelled && setName(data.name));
	return () => cancelled = true; }, [id]
);
```

_____

