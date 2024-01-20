____

tags: #React #Redux #bindActionCreators

`bindActionCreators()` - связывает функцию action creator с функцией `dispatch()`

`const { add, remove } = bindActionCreators(actions);`

Созданные таким способом функции делают сразу два действия - создание действия (action) и отправка action в dispatch().

_____

