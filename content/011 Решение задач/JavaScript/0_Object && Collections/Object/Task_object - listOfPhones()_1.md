```js
const book = [
    {name: 'aaa', phones: [111,222,333]},
    {name: 'bbb', phones: [444,555,222]},
    {name: 'ccc', phones: [333]},
    {name: 'ddd', phones: [777]}
]

// aaa, bbb: 222
// aaa, ccc: 333

function listOfPhones (book, number = 0) {
    if(typeof book !== 'object') {
        throw new Error ('Проверяемый параметр не обьект!')
    }
    if(typeof Number(number) !== 'number') {
        throw new Error('Искомый номер не число!')
    }
    let newArr = [];
    
    for(let i = 0; i < book.length; i++) {
        if(book[i].phones.find(number)) {
            newArr.push(book[i].name)
        }
    }
    
    return `${newArr.join(', ')}: ${number}`
}

console.log(listOfPhones(book, 222))
console.log(listOfPhones(book, 333))
```