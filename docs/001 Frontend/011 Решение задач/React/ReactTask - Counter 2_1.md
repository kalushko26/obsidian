---
title: ReactTask - Counter 2_1
draft: false
tags:
  - "#JavaScript"
  - "#taskJS"
  - "#альфабанк"
  - "#useEffect"
  - "#useState"
---
[Реализуй Counter()](https://codesandbox.io/s/reacttask-counter-2-1-sxr78t?file=/src/App.js)

```jsx
import { useEffect, useState } from "react";
import "./styles.css";

export default function App() {
  const [count, setCount] = useState(0);

  const increment = () => {
    setCount(count + 10);
  };

  const decrement = () => {
    setCount(count - 10);
  };

  useEffect(() => {
    decrement, increment;
  }, [increment, decrement, count]);

  return (
    <div className="App">
      <h1>Counter</h1>
      <h2>{count}</h2>
      <button onClick={decrement}>DEC</button>
      <button onClick={increment}>INC</button>
    </div>
  );
}
```

___

[[011 Решение задач JS, TS и React|Назад]]