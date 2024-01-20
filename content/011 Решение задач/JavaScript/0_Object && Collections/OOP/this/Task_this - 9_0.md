tags: #JavaScript #this #taskJS 
___

```js
"use strict";

const obj1 = {
    name: "Alice",
    func1: () => {
        return () => {
            console.log(this.name);
        };
    },
};

const obj2 = {
    name: "Bob",
    func2: obj1.func1(),
};

obj2.func2(); // und
```

### Ответ

```js

```

___
### [[011 Решение задач JS, TS и React|Назад]]