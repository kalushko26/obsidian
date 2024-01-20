____

tags: #React #Redux #mapDispatchToProps

```jsx
mapDispatchToProps - второй аргумент для функции #connect :

const mapDispatchToProps = (dispatch) => {
	return {
		inc: () => dispatch({ type: 'INC' } ) 
		};
};
```

Созданные функции будут переданы в компонент . 
Таким способом компонент может обновить состояние в #store .

_____
