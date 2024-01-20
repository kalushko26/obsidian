tags: #JavaScript #this #taskJS 
____

```js
function foo(num) {
	console.log('foo', num);
	this.count++;
}

foo.count = 0;

var i;
for (i = 0; i < 10; i++) {
	if (i > 5) foo(i);
}

console.log(foo.count);. //
```

### Ответ

```js

```


___
### [[011 Решение задач JS, TS и React|Назад]]
