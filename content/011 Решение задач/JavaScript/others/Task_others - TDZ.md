tags: #JavaScript #taskJS #var #let #const #TDZ 
____

```js
//Что будет выводится в консоль?
let b = 5;

function foo(a = b, b) {
    console.log(a, b) //
}

foo(undefined, 2) //
```