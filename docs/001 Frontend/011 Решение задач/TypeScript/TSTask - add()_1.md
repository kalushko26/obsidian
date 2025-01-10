---
title: TSTask - add()_1
draft: false
tags:
  - "#TypeScript"
  - "#tsTask"
---
```ts
function add(x: string, y: string): string; 
function add(x: number, y: number): number { 
	return x + y; 
} 

add(’1’,’2’);
```

**Ответ

```ts
function add(x: string, y: string): string; 
function add(x: number, y: number): number;
function add(x: number | string, y: number | string): number | string {
    if(typeof x === 'number' & typeof y === 'number') {
        return x + y
    } else if (typeof x === 'string' & typeof y === 'string') {
        return x + y
        
    } else {
        throw new Error('Invalid types of arguments')
    }
}

add("1", "2")
```

___

[[011 Решение задач JS, TS и React|Назад]]