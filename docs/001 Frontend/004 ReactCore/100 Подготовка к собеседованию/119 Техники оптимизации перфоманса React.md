---
title: Техники оптимизации перфоманса React
draft: false
tags:
  - "#React"
  - "#shouldComponentUpdate"
  - "#useMemo"
info:
---
Вот несколько техник оптимизации производительности React:

* немутабельная структура данных;
* function/stateless components и React.PureComponent
* shouldComponentUpdate
* React.Fragments
* избегайте онлайновых функций в render
* Throttling и Debouncing
* использовать "key" для отрисовки элементов массива
* использование Reselect в Redux
* мемоизация компонентов (memo(), useMemo(), useCallback())
* использование Web Workers
* разбиение на "чанки"

---

[[004 ReactCore|Назад]]