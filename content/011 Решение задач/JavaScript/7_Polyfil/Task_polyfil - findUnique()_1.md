tags: #JavaScript #taskJS #polyfill #array #unknownINC 
____

```js
//Написать метод массива, который будет возвращать массив уникальных значений 

 Array.prototype.findUnique = function() {
	// Ваш код здесь
// };

 [10, 5, 10, 1, 6, 6, 6, 7, 9, 9, 10].findUnique();


// расширить массив методом findUnique, который возвращает новый массив, где перечислены только уникальные значения массива
[10, 5, 10, 6, 6, 7, 2, 9, 9, 'str', 'str', 'constructor', date, () => { }].findUnique(); 
// [5, 7, 2, date]

Array.prototype.findUnique = findUnique;
function findUnique() {
 // Ваш код здесь
}

const obj = {}
console.log(obj.key); // undefined obj[key]
console.log(obj.constructor); // function
```

### Ответ

```js
Array.prototype.findUnique = function() {
    return [...new Set(this)];  
};

[10, 5, 10, 1, 6, 6, 6, 7, 9, 9, 10].findUnique();


// расширить массив методом findUnique, который возвращает новый массив, где перечислены только уникальные значения массива

Array.prototype.findUnique = findUnique;

function findUnique() {
    
    const newObj = this.reduce((acc, el) => {
        if(typeof el !== 'string' && typeof el !== 'number') {
            "" + el
        }
        acc[el] = (acc[el] || 0) + 1
        return acc
    }, {});
    
    let uniqueArr = [];
    
    for(let key in newObj) {
        if(newObj[key] === 1) {
            uniqueArr.push(key)
        }
    }
    return uniqueArr
}

[10, 5, 10, 6, 6, 7, 2, 9, 9, 'str', 'str', 'constructor', 'date', () => { }].findUnique(); 
// [5, 7, 2, 'constructor', date]
```


___
### [[011 Решение задач JS, TS и React|Назад]]