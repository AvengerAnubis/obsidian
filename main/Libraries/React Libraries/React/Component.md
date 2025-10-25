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
## You can use [Hook|hooks] for accessing different features in your component
## Rendering lists - `array.map(data => <li>{data}</li>)`
## Keep component functions as [[Pure function|pure]]
## [[Component Architecture.canvas|Architecture]]

## Server Component - a component that renders at the server ahead of time before being shown to a user. Can run on a server to fetch static content or read from the filesystem.
### Code in the component function executes on server every render, so you can read static data or db once. It will be shown to all the users but the data will be obtained once while render happens.
## Client Component - a component being created on the client side, so it can't use static data from the server. It can only get it through fetching the data from server or api
### To ma