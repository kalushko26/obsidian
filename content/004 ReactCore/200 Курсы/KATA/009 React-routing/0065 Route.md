____

tags: #react #React-router #route

В Route можно передать render функцию
~~~jsx
<Route path="/hi" render={() => <p>Hi</p>} />
~~~

`Route` работает как фильтр - сравнивая `path` с текущим адресом он решает отрисовать содержимое или нет.

Параметр `exact` говорит, что нужно использовать точное совпадение (а не "path является частью адреса" )

~~~jsx
<Route 
	path="/" 
	render={() => <h2> Welcome to ...</h2>}} 
	exact 
/>
~~~

_____