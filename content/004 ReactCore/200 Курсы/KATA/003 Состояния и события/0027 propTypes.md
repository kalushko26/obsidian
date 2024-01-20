____

tags: #React #propTypes #props

Позволяет проверить значение свойств ( #props ) , которые получает компонент
~~~jsx
const Comp = ({name}) => (<p>{name}</p>);
	Comp.propTypes = {
		name: (props, propName, compName) => {...}
}
~~~

Проверка срабатывает после #defaultProps
функция-валидатор возвращает #null или объект #error 

_____

