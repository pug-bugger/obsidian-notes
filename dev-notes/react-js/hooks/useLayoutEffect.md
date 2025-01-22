Runs before the content gets painted on the screen.
That means that in case then want to get result before content is loaded you need to load data earlier than content is loaded.

Using same like useEffect:
```
useLayoutEffect(() => {
	function test() {
		if (counter === 0) {
			setCounter(Math.random() * 200)
		}
	}
	test()
}, [count])
```

