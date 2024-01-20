tags: #JavaScript #taskJS #альфабанк 
___

```js
/*
Есть массив операций
Необходимо операции отсортировать по дате и сгруппировать их по году, а в качестве значений представить массивы с датами в формате MM-DD.
Пример результаты:
result = {
	"2017": [
		"07-31",
		"08-22"
		],
	"2018": [
		"01-01",
		"02-22"
	]
}
*/

const operations = [
	{"date": "2017-07-31", "amount": "5422"},
	{"date": "2017-06-30", "amount": "5220"},
	{"date": "2017-05-31", "amount": "5365"},
	{"date": "2017-08-31", "amount": "5451"},
	{"date": "2017-09-30", "amount": "5303"},
	{"date": "2018-03-31", "amount": "5654"},
	{"date": "2017-10-31", "amount": "5509"},
	{"date": "2017-12-31", "amount": "5567"},
	{"date": "2018-01-31", "amount": "5597"},
	{"date": "2017-11-30", "amount": "5359"},
	{"date": "2018-02-28", "amount": "5082"},
	{"date": "2018-04-14", "amount": "2567"},
];

function sortOperations(operations){
	// Код функции здесь
}

```

### Ответ

```js
function sortOperations(operations){ 
	return operations.reduce((acc, el) => { 
		const year = new Date(el.date).getFullYear(); 
		if (acc[year]) { 
			acc[year].push(el.date.slice(5)); 
			acc[year].sort((a, b) => a > b ? 1 : -1); 
		} else { 
			acc[year] = [el.date.slice(5)]; 
		} 
		return acc; 
	}, {}); 
} 

console.log(sortOperations(operations));
```

```js
function sortOperations(operations){
    const operDate = {};
    
    for(let name of operations){
        let date = new Date(name["date"]);
        let day = date.getDate();
        let month = date.getMonth()+1;
        let year = date.getFullYear();
        
        if(month < 10) month = '0' + month
        if(day < 10) day = '0' + day
        
        if(operDate[year]){
            operDate[year].push(`${month}-${day}`);
            operDate[year].sort((a, b) => a > b ? 1 : -1);
        } else {
            operDate[year] = [`${month}-${day}`]
        }
    }
    return operDate
}

console.log(sortOperations(operations))
```

___
### [[011 Решение задач JS, TS и React|Назад]]