---
title: ReactTask - fetchData 1_1
draft: false
tags:
  - "#React"
  - "#reactTask"
  - "#fetch"
  - "#async"
  - "#сбербанк"
---
```jsx
/*
Есть компонент и функция fetchData() необходимо получить данные и отрисовать их в списке
*/

function fetchData() {
	fetch('api/tada.json');
}
// ['hello', 'again', 'hello', 'Just called to say hello']

function Component() {
	return <div />
}
```

```JSX
function fetchData() {
	fetch('api/tada.json')
		.then(response => response.json())
		.then(data => {
			// Вызовите функцию для отображения данных в списке
			renderList(data);
		})
		.catch(error => {
			// Обработка ошибки при получении данных
			console.error('Ошибка получения данных:', error);
		});
}

function renderList(data) {
	// Используйте полученные данные для отображения списка
	const listItems = data.map((item, index) => <li key={index}>{item}</li>);

	// Верните JSX-элемент, содержащий список
	return <ul>{listItems}</ul>;
}

function Component() {
	// Вызовите функцию fetchData() для получения данных
	fetchData();

	return <div>Загрузка данных...</div>;
}
```

___

[[011 Решение задач JS, TS и React|Назад]]