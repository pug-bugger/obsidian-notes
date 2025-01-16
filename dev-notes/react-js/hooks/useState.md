use state variable is an callout what render change only then value is changes.
To use
```
[count, setCount] = useState(0)
const increment = () => {
	setCount((prevCounter) => prevCounter + 1)
	setCount((prevCounter) => prevCounter + 1)
}

return (
	<div>
		<h1>{count}</h1>
		<button onClick={increment}>Increment count</button>
	</div>
)
```

