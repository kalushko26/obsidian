---
title: ReactTask - useRef_0
draft: false
tags:
  - "#React"
  - "#useRef"
  - "#useState"
  - "#reactTask"
  - "#астралСофт"
---
```jsx
const Child = ({ value }) => {
	return <p> {value} </p>
};

const Main = () => {
	const value = useRef(null);
	const handeChangeValue = () => {
		value.current = Math.random()
	};
	return (
		<section>
			<Child value={value.current}/>
			<button type='button' onClick={handeChangeValue}>
				Btn
			</button>
		</section>
	)
}

// Увидим ли мы актуальное value ?
```

**Ответ

Мы увидим неактуальное значение `value` потому что `useRef(null)` представляет собой пустое хранилище данных, которое передаётся в качестве `props` в компонент `Child`. В данном случае значение всегда будет `null`, исправленный код представлен ниже:

```jsx
import React, {useState} from 'react';
import Child from './Child';
import "./styles.css";

 const App = () => {
  const [value, setValue] = useState(0)
  
	const handeChangeValue = () => {
		setValue(() => Math.floor(Math.random()*1000))
  };
  
	return (
		<section>
			<Child value={value}/>
			<button type='button' onClick={handeChangeValue}>
				Btn
			</button>
		</section>
	)
}

export default App;
```

```jsx
import React from 'react';

const Child = ({ value }) => {
	return <p> {value} </p>
};
export default Child;
```

___

[[011 Решение задач JS, TS и React|Назад]]