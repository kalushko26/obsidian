tags: #JavaScript #taskJS #class #СИБУР 
___

```JS
class A {
    constructor() {
        this.name = "foo";
        this.getName();
    }

    getName() {
        console.log("foo " + this.name);
    }
}

class B extends A {
    constructor() {
        super();
        this.name = "bar";
        this.getName();
    }

    getName() {
        console.log("bar " + this.name);
    }
}

 new B()
```

### Ответ

```js
bar bar
foo bar
```

___
### [[011 Решение задач JS, TS и React|Назад]]