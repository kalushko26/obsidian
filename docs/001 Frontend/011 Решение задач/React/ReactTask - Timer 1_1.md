---
title: ReactTask - Timer 1_1
draft: false
tags:
  - "#React"
  - "#reactTask"
  - "#SignalINC"
---
[Условие:](https://codesandbox.io/s/new-test-tasks-part-1-forked-yll7c3?file=/src/2_test-timer-component.tsx) **Реализуйте таймер**

```jsx
import { useEffect, useState } from "react";

const Timer = () => {
  const [seconds, setSeconds] = useState(0);
  const [loaded, setLoaded] = useState(false)

  const getTime = () => {
    if(loaded) {
      setSeconds((seconds) => seconds + 1);
    }
  };

  const resetTime = () => {
    setLoaded(false)
    setSeconds(0);
  };

  const toggleTime = () => {
    setLoaded((prevLoaded) => !prevLoaded);
  };

  useEffect(() => {
    const interval = setInterval(() => getTime(), 1000);
    return () => clearInterval(interval);
  }, [loaded]);

  return (
    <div>
      <h2>seconds: {seconds}</h2>
      <button onClick={toggleTime}>Toggle</button>
      <button onClick={resetTime}>Reset</button>
    </div>
  );
};

export default Timer;
```

___

[[011 Решение задач JS, TS и React|Назад]]