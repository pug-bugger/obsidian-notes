To avoid many of re-renders (or api requests on each change, each character), we use useEffect()

```
useEffect(() => {
	// code to execute
}, [])
// [] means, that this code in array function will runs once then this componens was rendered
```

Lets write example of useEffect where code will be executed every time input useState value is changed.

```
const [input, setInput] = useState("")
useEffect(() => {
	// code to execute
}, [input])
// [] every time input is changed, code in array function will be executed

return(
	<div>
		<input onChange={() => setInput(e.target.value)} type="text"/>
	</div>
)
```
