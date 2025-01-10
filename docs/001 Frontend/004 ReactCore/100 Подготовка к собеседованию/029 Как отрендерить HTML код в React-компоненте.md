---
title: Как отрендерить HTML код в React-компоненте?
draft: false
tags:
  - "#React"
  - "#dangerouslySetInnerHTML"
  - "#XSS"
info:
  - https://dev.to/thawkin3/protecting-against-xss-attacks-in-react-441m
  - https://blog.logrocket.com/using-dangerouslysetinnerhtml-in-a-react-application/
---
В React для отображения HTML кода в компоненте можно использовать специальное свойство `dangerouslySetInnerHTML`. Это свойство позволяет установить HTML-код в качестве содержимого элемента, но при этом _требует максимальной осторожности при использовании, так как может привести к возникновению уязвимостей безопасности._ Возникает уязвимость для XSS-атак.

Для использования `dangerouslySetInnerHTML` в компоненте необходимо создать объект с ключом `__html`, значение которого будет содержать HTML-код, который вы хотите отобразить. Затем, этот объект можно передать в свойство `dangerouslySetInnerHTML`.

Например, чтобы отобразить HTML-код `<p>Hello, world!</p>` в компоненте `MyComponent`, мы можем использовать `dangerouslySetInnerHTML` следующим образом:

```jsx
class MyComponent extends React.Component {
  render() {
    const html = "<p>Hello, world!</p>"
    return <div dangerouslySetInnerHTML={{ __html: html }} />
  }
}
```

Здесь мы создаем объект `{ __html: html }`, содержащий наш HTML-код, и передаем его в свойство `dangerouslySetInnerHTML` компонента `div`. В результате, HTML-код будет отображен внутри компонента `div`.

_Обратите внимание, что использование `dangerouslySetInnerHTML` может привести к уязвимостям безопасности, так как позволяет вставлять произвольный HTML-код в компонент. Поэтому, рекомендуется использовать этот способ только в тех случаях, когда это действительно необходимо и когда вы уверены в безопасности вставляемого HTML-кода._

---

[[004 ReactCore|Назад]]