____
tags: #React #React-элемент 
_____

Подключение библиотек React:
```jsx
import React from 'react';
import ReactDOM from 'react-dom/client';
import './index.css';
```


#VirtualDOM  - то, почему React работает так быстро.

#ReactDOMRender () превращает React элементы в обычные браузерные #DOM элементы и рендерит их на странице.

~~~jsx
import React from 'react'; 
~~~

Если удалить эту строку кода, то наше #React приложение не отобразится.

**Failed to compile 
'React' must be in scope when using JSX**

Перед тем, как наш код дойдет до браузера #babel должен преобразовать его в эквивалентный JS код.