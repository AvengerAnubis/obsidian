## A piece of [[UI]] optionally with logic in it
## Can [[useState|use state]]
## Structure:
```jsx
//imports
//functions and stuff

export default function Component({props, moreProps, children /*all elements placed inside the component as content*/}){
	//do something
	const [state, setState] = useState(0);
	return (
		//return markup HTML elements
		<div>
			<OtherComponent someData={state} /*JS code in curly brackets*/>
				Hello World!
				{children}
			</OtherComponent>
		</div>
	);
}
```
## Can return null sometimes (nothing to render)
## Rendering lists - `array.map(data => <li>{data}</li>)`
## Keep component functions as [[Pure function|pure]]
## [[Component Architecture.canvas|Architecture]]
