---
title: TSTask - rollDice()_1
draft: false
tags:
  - "#TypeScript"
  - "#tsTask"
  - "#СравниРУ"
---
```ts
// Типизируй функцию

function rollDice(): 1 | 2 | 3 | 4 | 5 | 6 { 
	return (Math.floor(Math.random() * 6) + 1); 
}
```

**Ответ

```ts
function rollDice():number { 
  return (Math.floor(Math.random() * 6) + 1); 
}

console.log(rollDice())
```

___

[[011 Решение задач JS, TS и React|Назад]]