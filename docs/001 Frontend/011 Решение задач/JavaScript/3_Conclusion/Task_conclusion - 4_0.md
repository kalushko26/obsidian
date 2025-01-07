---
title: Task_conclusion - 4_0
draft: false
tags:
  - "#JavaScript"
  - "#taskJS"
  - "#conclusion"
  - "#астон"
---
```js
var l = 25;
var x = 11;

function bar(foo) {
	var x = 30;
	foo()
}

function foo() {
	console.log('x', x) // x 11
}

foo.x = 20;
bar.x = 40;

bar(foo);

l.x = 100;

console.log('foo.x', foo.x) // х 20
console.log(bar.l) // undefined
console.log(l.x) // undefined
```

**Ответ

```js

```

___

[[011 Решение задач JS, TS и React|Назад]]