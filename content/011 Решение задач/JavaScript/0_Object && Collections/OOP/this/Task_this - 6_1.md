tags: #JavaScript #taskJS #this #СИБУР 
___

```js
function printContext() {
    console.log(this);
}

const printContextBind = printContext.bind({ a: 1 }).bind({ a: 2 });
printContextBind() // 
printContextBind.call({a:3}) // 
new printContextBind() // 
```
### Ответ

```js
function printContext() {
  console.log(this); 
}

const printContextBind = printContext.bind({ a: 1 }).bind({ a: 2 });
printContextBind() // { a: 1 }
printContextBind.call({a:3}) // { a: 1 }
new printContextBind() // printContext{}
```

___
### [[011 Решение задач JS, TS и React|Назад]]