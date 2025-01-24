```
const titleRef = useRef()

useEffect(() => {
	console.log(titleRef.current.offsetHeight)
}, [])

return (
	<div>
		<h1 ref={totleRef}>Hello Ref</h1>
	</div>
)
```