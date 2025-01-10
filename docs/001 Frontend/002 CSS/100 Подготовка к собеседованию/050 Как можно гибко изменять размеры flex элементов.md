---
title: Как можно гибко изменять размеры flex элементов?
draft: false
tags:
  - "#CSS"
  - "#flex"
info:
  - https://developer.mozilla.org/ru/docs/Learn/CSS/CSS_layout/Flexbox
---
```css
article {
  flex: 1 200px;
}

article:nth-of-type(3) {
  flex: 2 200px;
}
```

Это просто означает, что каждому flex элементу сначала будет дано 200px от свободного места. Потом оставшееся место будет поделено в соответствии с частями пропорций.

---

[[002 CSS|Назад]]