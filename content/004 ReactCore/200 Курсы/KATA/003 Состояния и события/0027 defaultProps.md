____

tags: #React #defaultProps

`defaultProps` позволяет писать меньше кода для установления значения по-умолчанию для свойств. Например: 

~~~jsx
const Comp = ({ name }) => (<p> {name} </p>);
	
Comp.defaultProps = {
		name: 'Bob'
	}
~~~

_____
