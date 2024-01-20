tags: #JavaScript #taskJS #class 
___

```js
class First {
	constructor(type = "first") {
		this.type = type;
		this.init();
	}
	
	init() {
		console.log(this.type);
	}
}

class Second extends First {
	type = "second";
}
const first = new Second("foo"); //
const second = new Second(); //
second.init(); //
```

### Ответ

```js

```


___
### [[011 Решение задач JS, TS и React|Назад]]