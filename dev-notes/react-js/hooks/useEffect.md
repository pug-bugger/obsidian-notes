To avoid many of re-renders (or api requests on each change, each character), we use useEffect()

```
useEffect(() => {
	// code to execute
}, [])
// [] means, that this code in array function will runs once then this componens was rendered
```
