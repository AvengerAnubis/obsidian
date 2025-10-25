```jsx
import { useEffect } from 'react';

export default function MyComponent() {  
	useEffect(() => {  
		// Code here will run after *every* render  
	});  
	return <div />;  
}
```
## Code below will result into an infinite loop, because `useEffect` executes after every render and setting a state cause component to re-render
```jsx
const [count, setCount] = useState(0);  

useEffect(() => {  
	setCount(count + 1);  //Infinite loop
});
```
## You can specify dependencies as the second argument to skip re-running the Effect when none of those dependencies have changed
```jsx
useEffect(() => {  
	if (isPlaying) { // It's used here...  
		// ...  
	} else {  
	// ...  
	}  
}, [isPlaying]); // ...so it must be declared here!
// if isPlaying has changed, this effect runs
```
## Initially, `useEffect` runs twice (in development react) - once after initial render and second time after first remount that happen immediately after its initial mount
## So you should consider to add clean-up function to your effect
```jsx
useEffect(() => {  
	const connection = createConnection();  
	connection.connect();  
	return () => {  
		connection.disconnect();  
	};  
}, []);
```
## Don't fix double-running with refs
```jsx
const connectionRef = useRef(null);  
useEffect(() => {  
	// 🚩 This wont fix the bug!!!  
	if (!connectionRef.current) {  
		connectionRef.current = createConnection();  
		connectionRef.current.connect();  
	}  
}, []);
```