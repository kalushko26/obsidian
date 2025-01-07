---
title: Какие by-функции вы знаете в Jest?
draft: false
tags:
  - testing
  - Jest
  - react-testing-library
  - getByText
  - getByRole
  - getByLabelText
  - getByPlaceholderText
  - getByAltText
  - getByTestId
---
В Jest, в контексте использования библиотеки `react-testing-library`, нет прямых "by-функций". Однако, `react-testing-library` предоставляет набор функций для поиска элементов в DOM, которые обычно начинаются с префикса `getBy`, `queryBy`, `findBy`, и т.д. Эти функции могут быть использованы для поиска элементов по различным критериям, таким как текст, роль, метка, плейсхолдер и другие.

Примеры таких функций:

- `getByText` - поиск по тексту
    
- `getByRole` - поиск по aria роли, явной или неявной
    
- `getByLabelText` - поиск элементов по атрибуту Label
    
- `getByPlaceholderText` - поиск элементов по атрибуту placeHolder
    
- `getByAltText` - поиск элементов по атрибуту alt
    
- `getByTestId` - поиск элементов по атрибуту data-testId
    

Эти функции помогают тестировать компоненты React более надежно и соответствующим лучшим практикам доступности.

____

[[007 Jest, RTL|Назад]]