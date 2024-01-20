____

tags: #React #Hooks 

#Hooks дают возможность компонентам-функциям работать со состоянием , жизненным циклом и контекстом .

```jsx
const HookSwitcher = () => {
	const [ num , setNum ] = useState (42);
	return <button onClick={setNum(100)}>{num}...
}
```
_____

