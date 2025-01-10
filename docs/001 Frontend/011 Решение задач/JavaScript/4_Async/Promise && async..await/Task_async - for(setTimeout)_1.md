---
title: Task_async - for(setTimeout)_1
draft: false
tags:
  - "#JavaScript"
  - "#taskJS"
  - "#астон"
  - "#for"
  - "#async"
---
```js
for (var i = 0; i < 10; i++) {
	setTimeout(function() {
	console.log(i)
	}, 1000)
}

// 10..... потому что сработает после выполнения синхронного кода, особенности var
// если let то 1, 2, 3, 4,
```

**Ответ

```js

```

___

[[011 Решение задач JS, TS и React|Назад]]