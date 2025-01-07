---
title: Task_string - isPerfect()_1
draft: false
tags:
  - "#JavaScript"
  - "#taskJS"
  - "#string"
---
```js
/*
Создайте функцию isPerfect(), которая принимает число и возвращает true, 
если оно совершенное, и false — в ином случае.

Совершенное число — положительное целое число, равное сумме его положительных делителей (не считая само число). 
Делитель — это число, на которое делится исходное число. 
Например, у числа 6 три делителя: 1, 2 и 3. Число 6 делится на любое из этих чисел. 
Так же 6 — идеальное число, потому что 6 = 1 + 2 + 3.

isPerfect(6); // true
isPerfect(7); // false
От себя - посмотри какие еще числа являются совершенными, чтобы на них тоже свое решение протестить
*/

const isPerfect = (num) => {
    if(num < 0) return false
    const arr = Object.keys(Array.from({length: num}));
    const newArr = [];
    
    for(let i = 0; i < arr.length; i++) {
        if(num > arr[i] && num % arr[i] === 0){
            newArr.push(Number(arr[i]))
        }
    }
    return newArr.reduce((acc, el) => {
        acc += el
        return acc
    });
}

console.log(isPerfect(6)); // true
console.log(isPerfect(7)); // false
console.log(isPerfect(28)); // true
console.log(isPerfect(496)); // true
```

```js
const isPerfect = (num) => { 
	if (typeof num !== 'number') { 
		return undefined; 
	} 
	
	let sum = 0; 
	
	for (let i = 1; i < num; i++) { 
		num % i === 0 ? sum += i : sum; 
	} 
	
	return num === sum; 
};
```

___

[[011 Решение задач JS, TS и React|Назад]]