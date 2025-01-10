---
title: TSTask - getUrls()_0
draft: false
tags:
  - "#TypeScript"
  - "#tsTask"
  - "#promise"
  - "#SignalINC"
---
```TS
/**
Необходимо реализовать функцию, которая опросит урлы и вернет массив ответов
['url1_answer', 'url2_answer', ...] так, чтобы в любой момент времени выполнялось не более limit запросов (как только любой из них завершился, сразу же отправляется следующий)
*/

interface ResponseDataType {
  delay: number;
  data: string;
}
const asyncFetch = (url: string) =>
  new Promise<ResponseDataType>((resolve) => {
    const delay = Math.random() * 1000;
    setTimeout(() => {
      resolve({ delay, data: "result" + url });
    }, delay);
  });

const urlsToFetch = Array(30)
  .fill((i: number) => `/${i}/aadt`)
  .map((fn, index) => fn(index));
```

**Ответ

```ts
/** Решение задачи                */
const paralellUploading = (
  urls: string[],
  parallelLimit: number
): Promise<ResponseDataType[]> => {
  throw new Error("notImplemented");
};

const responsArr = paralellUploading(urlsToFetch, 3);
console.log(responsArr);
```


___

[[011 Решение задач JS, TS и React|Назад]]