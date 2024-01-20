____

tags: #react #React-router 

Компоненты `Switch` оборачивает другие компоненты (`Route` и `Redirect`)

~~~jsx
<Switch>
	<Route path="/books" ... />
	<Route path="/blog" ... />
</Switch>
~~~

Switch отрисует только первый элемент, который соответствует адресу 
Route без свойства path срабатывает всегда .

_____

