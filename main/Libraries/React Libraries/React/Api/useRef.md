## Ref does NOT triggers new render on changes
```jsx
import { useRef } from 'react';

export default function SomeComponent(){
	let ref = useRef(0 /*some default value*/);
	
	function handleClick() {
	    ref.current = ref.current + 1; //does not cause rerender of the component
	    alert('You clicked ' + ref.current + ' times!');
	}

	return (
	    <button onClick={handleClick}>
		    Click me!
	    </button>
	);
}
```
`<div ref={myRef}>` cause `myRef` to store a reference to this `div` element