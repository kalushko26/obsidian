---
title: Task_whatif - 17_0
draft: false
tags:
  - "#JavaScript"
  - "#taskJS"
  - "#itOne"
---
```js
// №$@ня какая-то, он просто просил порассуждать на тему, почему не ререндерится ArticlesPage в рауте при переходе, но
// из кода показал только это:
// App.tsx
<Routes>
    <Route path="company" element={<CompanyPage/>}/>
    <Route path="pages/:article"
           element={<ArticlesPage />}/>
</Routes>

// ArticlesPage.tsx
export default ()=>{
    useEffect(() => {
        doFetch({
            method: 'GET',
            headers: {
                'Content-Type': 'application/json',
            },
        })
    }, [doFetch, location.key])
    return (
        <ArticleContext.Provider value={{article, setArticle}}>
            .....
        </ArticleContext.Provider>
    )
}
```

**Ответ

```js

```

___

[[011 Решение задач JS, TS и React|Назад]]