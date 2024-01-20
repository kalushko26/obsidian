____

tags: #React #setState 

links: [[0017 Как работает setState]]

setState() — удалить элемент > setState() не должен изменять текущий state 
> методы, которые изменяют (mutate) массив использовать нельзя 
> > newArr = [ …oldArr.slice(0, idx), …oldArr.slice(idx 1) ]; 
> > // не изменяет oldArr

_____

