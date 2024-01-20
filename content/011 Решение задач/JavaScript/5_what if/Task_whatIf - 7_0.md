tags: #JavaScript #taskJS 
____

```js
var b = {
  p: "b",
  b: function () {
    console.log(this.p);
  },
};

var a = {
  p: "a",
  a: function () {
    var b1 = b.b;
    a.b2 = b1;
    b1();  
    b.b();  
    a.b2(); 
  },
};
a.a();
```

### Ответ

```js

```

___
### [[011 Решение задач JS, TS и React|Назад]]