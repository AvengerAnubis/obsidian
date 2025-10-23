## Creating context
```jsx
import { createContext } from 'react';

export const LevelContext = createContext(1);
```
## Using context
```jsx
import { useContext } from 'react';
import { LevelContext } from './LevelContext.js';
//...
export default function Heading({ children }) {
	const level = useContext(LevelContext);
	//... return something ...
}
```
## Providing context
```jsx
import { LevelContext } from './LevelContext.js';  

export default function Section({ level, children }) {  
	return (  
		<section className="section">  
			<LevelContext value={level}>  
				{children}  
			</LevelContext>  
		</section>  
	);  
}
```
## Every `children` inside `LevelContext` will get the context value provided inside the `value` prop