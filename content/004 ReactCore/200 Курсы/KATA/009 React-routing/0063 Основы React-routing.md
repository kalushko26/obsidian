____

tags: #react #React-router 

links: https://v5.reactrouter.com/web/guides/quick-start

![React Router 6 - базовый роутинг React-приложения](https://www.youtube.com/watch?v=0auS9DNTmzE&list=PLiZoB8JBsdznY1XwBcBhHL9L7S_shPGVE)

```bash
npm i --save react-router-dom
```

Пример #React-routing для приложения :

~~~jsx
import { browserRouter as Router, Route } from 'react-router-dom';

<Router>
	<Route path="/blog" component={blog} />
	<Route path="/about" component={about} />
	<Route path="/shop" component={shop} />	
</Router>
~~~

*React Router* - это не часть React . 
Есть и другие библиотеки для роутинга ( к примеру , UI-Router)

_____

