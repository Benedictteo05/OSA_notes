"Too many re-renders. React limits the number of renders to prevent an infinite loop"
- To solve it, pass the function causing the problem as a callback function.
```
const [Count, setCount] = useState(0)

// Mistake
<button onClick={setCount(Count + 1)}>Increment</button>

// Solution
<button onClick={() => setCount(Count + 1)}>Increment</button>

```
