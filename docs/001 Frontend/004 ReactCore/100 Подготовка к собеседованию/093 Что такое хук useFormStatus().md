---
title: Что такое хук useFormStatus() ?
draft: false
tags:
  - React
  - Hooks
  - useFormStatus
  - React19
info:
  - https://react.dev/reference/react-dom/hooks/useFormStatus
  - https://dev.to/logrocket/understanding-reacts-useformstate-and-useformstatus-hooks-2oh1
---
В дизайн-системах часто требуется писать компоненты дизайна, которым нужен доступ к информации о `<form>`, в котором они находятся, без прокидывания пропсов вниз по дереву компонентов. Это можно сделать через Context, но чтобы упростить общий случай, мы добавили новый хук `useFormStatus`:

```javascript
import { useFormStatus } from 'react-dom';

function DesignButton() {
  const { pending } = useFormStatus();
  return <button type="submit" disabled={pending} />
}
```

`useFormStatus` считывает статус родительской `<form>`, как если бы форма была провайдером Context.

___

[[004 ReactCore|Назад]]