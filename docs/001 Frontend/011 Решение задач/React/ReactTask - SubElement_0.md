---
title: ReactTask - SubElement_0
draft: false
tags:
  - "#React"
  - "#reactTask"
  - "#itOne"
---
```jsx
const ParentElement = ()=>{
    const [count, setCount] = useState(0)
    const increment = () => setCount((prevProps) => ++prevProps);
    return(
      <>
        Parent: {count}  <br/>
        <SubElement clicker={increment} count={count}/>
    </>)
  }
  
  const SubElement = ({clicker, count})=>{
    return (
      <>
      Sub: {count}
      <button onClick={clicker}>Increment</button>
      </>)
  }
```

**Ответ

```jsx
// юзать React.memo + его второй параметр (аналог shouldComponentUpdate ) (ответ ниже)

  const SubElement = React.memo(({clicker, count})=>{
    return (
      <>
      Sub: {count}
      <button onClick={clicker}>Increment</button>
      </>)
  }, (prevProps, newProps)=> newProps.count % 2 !== 0)
```

___

[[011 Решение задач JS, TS и React|Назад]]