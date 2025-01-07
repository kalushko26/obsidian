---
title: ReactTask - Timer 2_1
draft: false
tags:
  - "#React"
  - "#reactTask"
  - "#unknownINC"
  - "#itOne"
---
[Условие:](https://codesandbox.io/s/silent-worker-ssd8ly?file=/src/index.js:109-123)

```jsx
import React, { useEffect, useState } from "react";
import { createRoot } from "react-dom/client";

import "./styles.css";

function TimerContainer() {
  let [isTimerStarted, setTimerStarted] = useState(false);

  const startTimer = () => setTimerStarted(true);

  const stopTimer = () => setTimerStarted(false);

  return (
    <div className="App">
      <div>
        <Timer
          isStarted={isTimerStarted}
          onStop={stopTimer}
        />
      </div>
      <button onClick={startTimer}>Start</button>
      <button onClick={stopTimer}>Stop</button>
    </div>
  );
}

function Timer({ isStarted, onStop }) {
  const [seconds, setSeconds] = useState(0);
  const [fibb, setFibb] = useState(0);

  const fibbonachi = (n) => {
    if (n <= 1) return n;
    return fibbonachi(n - 1) + fibbonachi(n - 2);
  };

  useEffect(() => {
    const interval = setInterval(() => {
      setSeconds((prevSeconds) => prevSeconds + 1);
      setFibb(fibbonachi(seconds));
    }, 1000);

    if (!isStarted) {
      clearInterval(interval);
      onStop();
    }

    return () => clearInterval(interval);
  }, [seconds, isStarted, onStop]);

  return (
    <>
      <h2>Fibbonachi: {fibb}</h2>
      <h2>Seconds: {seconds}</h2>
    </>
  );
}

const rootElement = document.getElementById("root");
const root = createRoot(rootElement);

root.render(<TimerContainer />);
```

___

[[011 Решение задач JS, TS и React|Назад]]