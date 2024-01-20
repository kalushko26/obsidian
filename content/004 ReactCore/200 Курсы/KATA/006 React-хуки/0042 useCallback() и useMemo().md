____

tags: #React #Hooks #useCallback #useMemo


* `useCallback()` - сохраняет функцию между вызовами, если данные в массиве зависимостей не изменились. 
// f - функция из первого аргумента
`const f = useCallback(() => loadData(id), [id]);`

* `useMemo()` - работает также, но для значений.
// v - результат функции из первого аргумента
`const v = useMemo(() => getValue(id) , [id]);`

_____

