---
title: ReactTask - useDebounce()_0
draft: false
tags:
  - "#React"
  - "#reactTask"
  - "#usedebounce"
  - "#Debounce"
  - "#itOne"
---
// Написать кастомный хук `useDebounce()`

```jsx
import React, { useState, useEffect } from "react";

const useDebounce = (value, delay) => {
  const [debouncedValue, setDebouncedValue] = useState(value);

  useEffect(() => {
    const timer = setTimeout(() => {
      setDebouncedValue(value);
    }, delay);

    return () => {
      clearTimeout(timer);
    };
  }, [value, delay]);

  return debouncedValue;
};

export default function App() {
  const [inputValue, setInputValue] = useState("");
  const debouncedInputValue = useDebounce(inputValue, 500);

  const handleChange = (event) => {
    setInputValue(event.target.value);
  };

  return (
    <div className="App">
      <input type="text" value={inputValue} onChange={handleChange} />
      <p>Debounced Value: {debouncedInputValue}</p>
    </div>
  );
}
```

___

[[011 Решение задач JS, TS и React|Назад]]