---
title: Что такое хук useOptimistic() ?
draft: false
tags:
  - React
  - Hooks
  - useOptimistic
  - React19
info:
  - https://react.dev/reference/react/useOptimistic
---
Другой распространенный шаблон UI при выполнении мутации данных — это оптимистичное отображение конечного состояния во время выполнения асинхронного запроса. В React 19 мы добавляем новый хук под названием `useOptimistic`, чтобы упростить это:

```javascript
function ChangeName({ currentName, onUpdateName }) {
  const [optimisticName, setOptimisticName] = useOptimistic(currentName);

  const submitAction = async formData => {
    const newName = formData.get("name");
    setOptimisticName(newName);
    const updatedName = await updateName(newName);
    onUpdateName(updatedName);
  };

  return (
    <form action={submitAction}>
      <p>Ваше имя: {optimisticName}</p>
      <p>
        <label>Изменить имя:</label>
        <input
          type="text"
          name="name"
          disabled={currentName !== optimisticName}
        />
      </p>
    </form>
  );
}
```

Хук `useOptimistic` немедленно отобразит `optimisticName`, пока запрос `updateName` выполняется. Когда обновление завершится или произойдет ошибка, React автоматически вернется к значению `currentName`.

___

[[004 ReactCore|Назад]]
