tags: #JavaScript #taskJS #EventLoop #СИБУР 
____

```JS
//! что будет в консоли, что выполнится

function task1() {
    console.log(1);

    setTimeout(function () {
        console.log(2);
    }, 0);

    const p = new Promise((resolve, reject) => {
        console.log(3);
        setTimeout(() => {
            resolve();
            reject();
        });
    });

    p.then(() => {
        console.log(4);
    }).catch(() => {
        console.log(5);
    });

    console.log(6);
}

task1();
```

___
### [[011 Решение задач JS, TS и React|Назад]]
