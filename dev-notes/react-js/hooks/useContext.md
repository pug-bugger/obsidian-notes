
```
const CounterContext = createContext()

const CounterProvider = ({ children }) {
	const [count, setCount] = useState(0)
	const increment = () => setCount((counter) => counter + 1)
	
	const contexValue = {
		count,
		increment
	}
	
	return(
		<CounterContext.Provider value={contextValue}>
			{children}
		</CounterContext.Provider>
	)
}
```