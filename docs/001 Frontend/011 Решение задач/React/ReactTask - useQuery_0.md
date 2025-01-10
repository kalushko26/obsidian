---
title: ReactTask - useQuery_0
draft: false
tags:
  - "#React"
  - "#reactTask"
  - "#Hooks"
  - "#unknownINC"
---
```jsx
//Написать хук useQeury который принимает url и возвращает 3 состояния запроса 
const {isLoading, error, data} = useQeury('https://jsonplaceholder.typicode.com/todos/1')
```

**Ответ

```jsx
const useQeury = (url) => {
  const [isLoading, setIsLoading] = useState(true);
  const [data, setData] = useState(null);
  const [error, setError] = useState(false);

  async function getResponse() {
    const response = await fetch(url);
    return response.json();
  }

  useEffect(() => {
    getResponse()
      .then((data) => setData(data))
      .catch((e) => setError(e))
      .finally(() => setIsLoading(false));
  }, [url]);

  return { isLoading, data, error };
};
```

___

[[011 Решение задач JS, TS и React|Назад]]