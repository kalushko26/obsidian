____

tags: #React #Hooks #useEffect 

```jsx
useEffect(() => console.log('mount') , [] );
useEffect(() => console.log('update'));
useEffect(() => () => console.log('unmount'), []);

// effect + cleanup ( mount + unmount )
useEffect(() => {
	const timeout = setTimeout(setVisible, 10, false);
	return () => clearTimeout(timeout);
}, []);
```

_____
