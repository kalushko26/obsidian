---
title: Для чего используется атрибут `enterkeyhint`?
draft: false
tags:
  - "#HTML"
  - "#enterkeyhint"
info:
---
![[Pasted image 20230704021934.png|600]]

Атрибут `enterkeyhint` используется для указания браузеру, какой тип действия пользователь ожидает выполнить, когда он нажимает клавишу "Enter" в форме на веб-странице.

Когда пользователь вводит данные в форму на веб-странице, он может нажать клавишу "Enter", чтобы отправить данные или перейти к следующему полю формы. По умолчанию браузер выбирает, какое действие выполнить при нажатии клавиши "Enter", основываясь на контексте и типе элемента формы.

Атрибут `enterkeyhint` позволяет явно указать браузеру, какое действие должно быть выполнено при нажатии клавиши "Enter". Этот атрибут может иметь следующие значения:

- `enter`: указывает, что при нажатии клавиши "Enter" должно быть выполнено действие по умолчанию для элемента формы, например, отправка формы.
- `go`: указывает, что при нажатии клавиши "Enter" должно быть выполнено действие "Перейти" (например, перейти на другую страницу).
- `search`: указывает, что при нажатии клавиши "Enter" должен быть выполнен поиск.
- `send`: указывает, что при нажатии клавиши "Enter" должно быть выполнено действие "Отправить" (например, отправить сообщение или письмо).
- `next`: указывает, что при нажатии клавиши "Enter" должно быть переход к следующему полю формы.
- `done`: указывает, что при нажатии клавиши "Enter" должно быть выполнено действие "Готово" (например, завершение редактирования или заполнения).
- `previous`: указывает, что при нажатии клавиши "Enter" должно быть переход к предыдущему полю формы.
- `none`: указывает, что при нажатии клавиши "Enter" никакое действие не должно быть выполнено.

Например, следующий код использует атрибут `enterkeyhint` для указания браузеру, что при нажатии клавиши "Enter" должен быть выполнен поиск:

```html
<form>
  <label for="search">Поиск:</label>
  <input type="text" id="search" name="search" enterkeyhint="search">
  <button type="submit">Искать</button>
</form>
```

Использование атрибута `enterkeyhint` может помочь улучшить пользовательский опыт и упростить навигацию в формах на веб-страницах.

---

[[001 HTML|Назад]]