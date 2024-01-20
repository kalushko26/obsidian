tags: #JavaScript #taskJS #polyfill #bind
___

```JS
// Напишите полифилл на bind
```

### Ответ

```js
Function.prototype.myBind = function(context, ...args) {
  return (...rest) => {
    return this.call(context, ...args.concat(rest))
  }
}

function log(...props) {
  console.log(this.name, this.age, ...props)
}

const obj = {name: 'Vladilen', age: 28}

log.myBind(obj, 1, 2)()
```


___
### [[011 Решение задач JS, TS и React|Назад]]