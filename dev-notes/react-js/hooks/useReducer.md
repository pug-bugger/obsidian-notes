```
const initialState = { backgroundColor: "#fff" }
const reducer = (state, action) => {
	switch (action) {
		case 'black':
			return {backgroundColor: '#000'}
		case 'red':
			return {backgroundColor: 'red'}
		default:
			return {backgroundColor: 'initial'}
	}
}

function App() {
	const [state,dispatch] = useReducer(reducer, initialState)
	return (
		<div>
			<h1 style={{ backgroundColor: state.backgroundColor }}>Hello</h1>
			<button onClick={() => dispatch('red')}>Turn to red</button>
			...
		</div>
	)
...
}
```

use better **ZUSTND**.
