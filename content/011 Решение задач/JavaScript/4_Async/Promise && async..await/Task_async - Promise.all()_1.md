tags: #JavaScript #taskJS #promise #promiseAll 
___

```js
const foo = (callback) => {
  setTimeout(() => {
    callback("A");
  }, Math.floor(Math.random() * 100));
};

const bar = (callback) => {
  setTimeout(() => {
    callback("B");
  }, Math.floor(Math.random() * 100));
};

const baz = (callback) => {
  setTimeout(() => {
    callback("C");
  }, Math.floor(Math.random() * 100));
};

const result = () => {};

result(); // ['C', 'A', 'B']
```

### Ответ

```js
const foo = (callback) => {
  setTimeout(() => {
    callback("A");
  }, Math.floor(Math.random() * 100));
};

const bar = (callback) => {
  setTimeout(() => {
    callback("B");
  }, Math.floor(Math.random() * 100));
};

const baz = (callback) => {
  setTimeout(() => {
    callback("C");
  }, Math.floor(Math.random() * 100));
};

const result = () =>
  Promise.all([new Promise(baz), new Promise(foo), new Promise(bar)]).then(
    console.log
  );

result(); // ['C', 'A', 'B']
```


___
### [[011 Решение задач JS, TS и React|Назад]]