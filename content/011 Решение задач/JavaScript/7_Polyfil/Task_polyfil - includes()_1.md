tags: #JavaScript #taskJS #polyfill #includes #БКС 
___

```js
// Ваш код здесь
```

### Ответ

```js
Array.prototype.myIncludes = myIncludes;

function myIncludes(el) {
    
    for(let i = 0; i < this.length; i++) {
        if(el === this[i]){
            return true
        }    
    }
    return false
}

[1, 2, 3].myIncludes('cat')
[1, 2, 3, 'cat'].myIncludes('cat')

```

___
### [[011 Решение задач JS, TS и React|Назад]]