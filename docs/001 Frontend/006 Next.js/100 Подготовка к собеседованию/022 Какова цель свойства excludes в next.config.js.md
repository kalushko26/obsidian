---
title: Какова цель свойства `excludes` в next.config.js?
draft: false
tags:
  - NextJS
  - next-config
  - excludes
info:
  - https://nextjs.org/docs/pages/api-reference/next-config-js/output
  - https://stackoverflow.com/questions/71305497/how-to-exclude-test-files-in-next-js-during-build
---
Свойство `excludes` в файле `next.config.js` используется для указания шаблонов файлов и директорий, которые должны быть исключены из автоматического разделения кода и объединения, выполняемых Next.js. Определяя шаблоны исключений, разработчики могут контролировать, какие файлы не подлежат стандартному поведению разделения кода.

Вот пример того, как свойство `excludes` может быть использовано в `next.config.js`:

```javascript
// next.config.js
module.exports = {
  excludes: ['/path/to/excluded/file.js', /\/node_modules\//],
  // другие конфигурации...
}
```

___

[[006 Next.js|Назад]]