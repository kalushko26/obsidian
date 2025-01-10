---
title: Квизы на понимание `this`
draft: false
tags:
  - "#JavaScript"
  - "#object"
  - "#this"
info:
  - https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Operators/this
---
## Квиз №1

### Вопрос

Что будет результатом за`проса?

```javascript
const call = {
  caller: "mom", 
  says: function() {
    console.log(`Hey, ${this.caller} just called.`);
  }
};

call.says();
```

Что вышеприведенный код будет выводить на консоль?  
  
(A) Hey, undefined just called.  
(B) Hey, mom just called.  
(C) Hey, caller just called.

### Ответ

**(B) Hey, mom just called.**  

```javascript
const call = {
  caller: "mom", 
  says: function() {
    console.log(`Hey, ${this.caller} just called.`);
  }
};

call.
```

Здесь у нас есть объявление функции внутри объекта call. Как правило, *"this"* определяется объектом, вызывающим функцию. Следовательно, когда объект call вызывает функцию says (call.says()), ключевое слово *'this'* внутри функции says ссылается на объект call, делая this.caller равным "mom".  
  
Довольно прямолинейно, не так ли?

## Квиз №2

### Вопрос

Что будет результатом запроса?

```javascript
const call = {
  caller: "mom", 
  says: () => {
    console.log(`Hey, ${this.caller} just called.`);
  }
};

call.says();
```

What will the code above log to the console?

(A) Hey, undefined just called.  
(B) Hey, mom just called.  
(C) Hey, caller just called.

### Ответ

**(A) Hey, undefined just called.**

```javascript
const call = {
  caller: "mom", 
  says: () => {
    console.log(`Hey, ${this.caller} just called.`);
  }
};

call.says();
```

Подождите, разве этот код не такой же, как первый?  
  
Если вы присмотритесь повнимательнее, объявление функции из задачи № 1 теперь заменено функцией со стрелкой.  
  
Функции со стрелками, как часть синтаксиса ES6, не имеют своего собственного ключевого слова *'this'*. Вместо этого они будут использовать ключевое слово 'this' для любого *"this"*, которое было вне функции, когда оно было создано.

Другими словами, '*this'* внутри функции arrow не привязан к нашему объекту call, но вместо этого уже привязан к тому месту, где изначально создается объект call, который в данном случае является глобальным объектом. И поскольку глобальный объект ничего не знает о функции say(), *'this'* не определено. И поскольку глобальный объект не имеет свойства caller, this.caller не определен.

## Квиз №3

### Вопрос

Что будет результатом запроса?

```javascript
const call = {
  caller: "mom", 
  says: function() {
    console.log(`Hey, ${this.caller} just called.`);
  }
};

let newCall = call.says;

newCall();
```

(A) Hey, undefined just called.  
(B) Hey, mom just called.

### Ответ

**(A) Hey, undefined just called.**

```javascript
const call = {
  caller: "mom", 
  says: function() {
    console.log(`Hey, ${this.caller} just called.`);
  }
};

let newCall = call.says;

newCall();
```

Здесь мы объявляем новую переменную newCall и присваиваем функции says внутри объекта call значение newCall. И затем мы вызываем newCall, который теперь является простым вызовом функции.  
  
Обратите внимание, где мы вызываем функцию. Находится ли это внутри объекта вызова? Нет. Мы вызываем функцию newCall() глобально, что, в свою очередь, делает ключевое слово *'this'* равным глобальному объекту.  
  
Как показано в задаче №2, поскольку глобальный объект не имеет вызывающего свойства, в результате вы получаете "undefined".  
  
К настоящему времени вы, возможно, заметили ключевую закономерность:  
Обычные функции изменяют свое поведение В ЗАВИСИМОСТИ ОТ объекта, ВЫЗЫВАЮЩЕГО функцию.

## Квиз №4

### Вопрос

Что будет результатом запроса?

```javascript
function anotherCaller() {
  console.log(`${this.caller} called, too!`);
}

const call = {
  caller: "mom", 
  anotherCaller: anotherCaller,
  says: function() {
    console.log(`Hey, ${this.caller} just called.`);
  }
};

let newCall = call.anotherCaller;

newCall();
```

(A) mom called, too!  
(B) Hey, mom just called.  
(C) undefined called, too!

### Ответ

**(C) undefined called, too!**

```javascript
function anotherCaller() {
  console.log(`${this.caller} called, too!`);
}

const call = {
  caller: "mom", 
  anotherCaller: anotherCaller,
  says: function() {
    console.log(`Hey, ${this.caller} just called.`);
  }
};

let newCall = call.anotherCaller;

newCall();
```

Мы вызываем функцию newCall() глобально, что означает, что ключевое слово *'this'* ссылается на глобальный объект. Не имеет значения, что мы присваиваем newCall функции внутри объекта call. Мы вызываем newCall глобально, и глобально - это то место, где назначено *"this"*.  
  
Если вам хочется приключений, попробуйте переместить функцию anotherCaller() внутри объекта call, например, так:

```javascript
const call = {
  caller: "mom", 
  anotherCaller: function() {
        console.log(`${this.caller} called, too!`)
      },
  says: function() {
    console.log(`Hey, ${this.caller} just called.`);
  }
};


let newCall = call.anotherCaller;
newCall();
```

Основываясь на том, что мы только что обсудили, как вы думаете, каким будет результат?  
  
Попробуйте мысленно запустить код, прежде чем проверять ответ в своем браузере. Если у вас получилось, то у вас получилось и это (по крайней мере, основы)!

Я надеюсь, что эти примеры дадут вам лучшее представление о том, как работает ключевое слово *"this"*. Если вы все еще находите это сбивающим с толку, не волнуйтесь. Как и во всем, что касается программирования, практика играет ключевую роль.  
  
Для получения дополнительных примеров ознакомьтесь с официальной документацией MDN. Я также настоятельно рекомендую эту потрясающую [статью](https://medium.com/m/global-identity-3?redirectUrl=https%3A%2F%2Fitnext.io%2Fthe-this-keyword-in-javascript-demystified-c389c92de26d)




## Квиз №5 

### Вопрос

Что будет результатом запроса?

```javascript
const object = {    
	message: 'Hello, World!',        
	getMessage() {    
		const message = 'Hello, Earth!';    
		return this.message;    
	}    
};        

console.log(object.getMessage()); // What is logged?            `
```

### Ответ

`'Hello, World!'` is logged to console. [Open the demo.](https://jsfiddle.net/dmitri_pavlutin/cmhv85g9/)

*object.GetMessage()* - это вызов метода, вот почему это внутри метода равно object.  
  
Внутри метода также есть объявление переменной const message = 'Привет, Земля!'. Переменная никак не влияет на значение this.message.

## Квиз №6

### Вопрос

Что будет результатом запроса?

```javascript
function Pet(name) {    
	this.name = name;        
	this.getName = () => this.name;    
}        

const cat = new Pet('Fluffy');        
console.log(cat.getName()); // What is logged?        
const { getName } = cat;    
console.log(getName()); // What is logged?            `
```

### Ответ

`'Fluffy'` and `'Fluffy'` are logged to console. [Open the demo.](https://jsfiddle.net/dmitri_pavlutin/k7em3bho/)

Когда функция вызывается как конструктор new Pet('Fluffy'), это значение внутри функции-конструктора равно созданному объекту.  
  
this.name = выражение name внутри конструктора Pet создает свойство name для созданного объекта.  
  
this.getName = () => this.name создает метод getName для созданного объекта. И поскольку используется стрелочная функция, это значение внутри функции равно значению внешней области видимости — функции конструктора Pet.  
  
Вызов cat.getName(), а также getName() возвращает выражение this.name это оценивается как "Fluffy".

## Квиз №7

### Вопрос

Что будет результатом запроса?

```javascript
const object = {    
	message: 'Hello, World!',        
	logMessage() {    
		console.log(this.message); // What is logged?    
	}    
};        

setTimeout(object.logMessage, 1000);            `
```

### Ответ

После задержки в 1 секунду undefined регистрируется в консоли. [Open the demo.](https://jsfiddle.net/dmitri_pavlutin/ducwj3e8/)
Хотя функция setTimeout() использует object.LogMessage в качестве обратного вызова, тем не менее, она вводит object.LogMessage как обычную функцию, а не метод.  
  
И во время обычного вызова функции это равно глобальному объекту, которым является window в случае среды браузера.  
  
Вот почему console.log(this.message) внутри метода LogMessage регистрирует window.message, который не определен.  
  
Побочная задача: как вы можете исправить этот код так, чтобы "Привет, мир!" регистрировался в консоли? Напишите свое решение в комментарии ниже!

## Квиз №8

### Вопрос

Что будет результатом запроса?

Как вы можете вызвать функцию LogMessage так, чтобы она регистрировала `"Hello, World!"`?

```javascript
const object = {    
	message: 'Hello, World!'    
};        

function logMessage() {    
	console.log(this.message); // "Hello, World!"    
}        

// Write your code here...            `
```

### Ответ

Существует по крайней мере 3 способа вызвать *LogMessage()* в качестве метода для объекта. Любой из них считается правильным ответом:

```javascript
const object = {    
	message: 'Hello, World!'    
};        

function logMessage() {    
	console.log(this.message); // logs 'Hello, World!'    
}        

// Using func.call() method    
logMessage.call(object);        

// Using func.apply() method    
logMessage.apply(object);        

// Creating a bound function    
const boundLogMessage = logMessage.bind(object);    
boundLogMessage();
```

[Open the demo.](https://jsfiddle.net/dmitri_pavlutin/0oubpzje/)

## Квиз №9

### Вопрос

Что будет результатом запроса?

Какие результаты выводятся в консоли в следующем фрагменте кода

```javascript
const object = {    
	who: 'World',        
	greet() {    
		return `Hello, ${this.who}!`;    
	},        
	farewell: () => {    
		return `Goodbye, ${this.who}!`;    
	}    
};        

console.log(object.greet()); // What is logged?    
console.log(object.farewell()); // What is logged?

```

### Ответ

`'Hello, World!'` and `'Goodbye, undefined!'` are logged to console. [Open the demo.](https://jsfiddle.net/dmitri_pavlutin/o4gsLyfe/)

При вызове object.greet() внутри метода greet() это значение равно object, потому что greet - это обычная функция. Таким образом, object.greet() возвращает 'Привет, Мир!'.  
  
Но farewell() - это функция со стрелкой, поэтому это значение внутри функции со стрелкой всегда равно значению внешней области видимости.  
  
Внешняя область действия farewell() - это глобальная область, где это глобальный объект. Таким образом, object.farewell() фактически возвращает 'До свидания, ${window.кто}!", который оценивается как "До свидания, не определено!".

## Квиз №10

### Вопрос

Что будет результатом запроса?

```javascript
var length = 4;    
function callback() {    
	console.log(this.length); // What is logged?    
}        

const object = {    
	length: 5,    
	method(callback) {    
		callback();    
	}    
};        

object.method(callback, 1, 2);            `
```

### Ответ

`4` is logged to console. [Open the demo.](https://jsfiddle.net/dmitri_pavlutin/Lr618c3s/)

*callback()* вызывается с помощью обычного вызова функции внутри *method().* Поскольку это значение во время обычного вызова функции равно глобальному объекту, *this.length* вычисляется как *window.length* внутри функции *callback()*.  
  
Первый оператор *var length = 4*, находящийся в самой внешней области видимости, создает свойство *length* для глобального объекта: *window.length* становится равной 4.  
  
Наконец, внутри функции *callback()*  *this.length* вычисляется как *window.length* — 4 регистрируется в консоли.

## Квиз №11

### Вопрос

Что будет результатом запроса?

```javascript
var length = 4;    
function callback() {    
	console.log(this.length); // What is logged?    
}        

const object = {    
	length: 5,    
	method() {    
		arguments[0]();    
	}    
};        

object.method(callback, 1, 2);            `
```

### Ответ

`3` is logged to console. [Open the demo.](https://jsfiddle.net/dmitri_pavlutin/ucat9ymL/1/)

`obj.method(callback, 1, 2)` is invoked with 3 arguments: `callback`, `1` and `2`. As result the `arguments` special variable inside `method()` is an array-like object of the following structure:

```javascript
{   
	0: callback,    
	1: 1,    
	2: 2,    
	length: 3    
} 
```

Because `arguments[0]()` is a method invocation of `callback` on `arguments` object, `this` inside the `callback` equals `arguments`. As result `this.length` inside `callback()` is same as `arguments.length` — which is `3`.