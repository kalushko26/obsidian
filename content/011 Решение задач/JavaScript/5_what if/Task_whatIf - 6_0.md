tags: #JavaScript #taskJS #IIFE 
____

```js
(function () {
  f();

  f = function () {
    console.log(1);
  };
})();

function f(){
  console.log(2)
}
f();

```

### Ответ

```js

```

___
### [[011 Решение задач JS, TS и React|Назад]]