---
title: В чем разница между tuple и массивом в TypeScript?
draft: false
tags:
  - "#TypeScript"
  - "#tuple"
  - "#array"
info:
---
Обычно `tuple` представляет собой фиксированного размера массив, состоящий из элементов известного типа. Порядок элементов должен соблюдаться.

```typescript
const primaryColors: [string, string, string] = [
	"#ff0000",
	"#00ff00",
	"#0000ff",
];
console.log(primaryColors);
```

_____

[[005 TypeScript|Назад]]