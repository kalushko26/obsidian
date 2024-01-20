____

tags: #react #withRouter #React-router 

#withRouter - это компонент высшего порядка , он передаёт компоненту объект react router :

~~~jsx
const MyComponent = ({ match , location , history }) => {
	return (
	<Button
		onclick={() => history.push(`/new/path`)}
	> Click ME </Button> );
};

export default withRouter(MyComponent)
~~~
_____

