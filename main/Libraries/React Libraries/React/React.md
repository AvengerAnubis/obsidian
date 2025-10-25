## The library for web and native user interfaces

## Summary
- ### [[UI|User interfaces]] as individual pieces named [[Component|components]]
- ### Combine them into complex components, screens, pages, apps
- ### Combine components made by others
- ### Components are JS functions
- ### Components use JSX syntax (HTML in JS)
## Thinking in React while creating an app
- ### Break UI into a component hierarchy (tree) ([[Component Hierarchy Example.canvas|example]])
- ### Building a static version of an app without any interactivity yet
- ### Find a minimal representation of UI state
	- #### Minimal data that an app needs to remember ([[DRY]])
	- #### Compute everything else
- ### Decide where the state should live
	- #### Find every component that uses that state
	- #### Create state ([[useState]]) in their closest common parent component
- ### Add inverse data flow (event listeners in inner components)
## Interactivity
- ### Event handles - onClick in default HTML components can be set to defined function inside the component
	```jsx
	export default function SomeComponent({prop}){
		function handleClick(){
			alert(`Hello ${prop}`);
		}
		return(
			<button onClick={handleClick}></button>
		);
	}
	```
- ### Event propagation - event handles can catch event from every children of the component
	- #### Stop propagation - `onClick={e => {
      e.stopPropagation(); //actions`
- ### Preventing default behaviour - `e.preventDefault();` inside event handler function
- ### State only changes on next render
- ### If you use objects as state, replace the objects itself instead of changing props in it
- ### Same with arrays
## Managing state
- ### Component should update its appearence (button visibility, etc.) by itslef based on state
- ### Avoid duplicates and possibility of impossible states
- ### Avoid deeply nested structure of state, use flat structure instead (with childIds or parentId)
- ### Move states up to common paretns
- ### State is tied to a position in the render tree
- ### Removing component from tree resets its state
- ### Same component at the same position preserves state
- ### Different components at the same position reset state
- ### Use [[useReducer|reducer]] instead of state in complex scenarios
- ### Use [[useContext|context]] if you want to provide a value deeply into the component tree
## Escape hatches
- ### Use [[useRef|ref]] if you want to store a variable outside of React and change it anytime without causing re-render of a component
- ### With ref you can manipulate the DOM tree directly
- ### Use [[useEffect|Effect]] to run code after rendering to sync a component with some system (database, API, built-in components like `<video>`, smth) outside of React:
	- #### Connections to DB or services
	- #### Subscribing to events
	- #### Triggering animations
	- #### Fetching data
	- #### Sending analytics
- ### Not a Effect use case:
	- #### Init the app
	```jsx
	if (typeof window !== 'undefined') { // Check if we're running in the browser.  
		checkAuthToken();  
		loadDataFromLocalStorage();  
	}  

	function App() {  
		// ...
	}
	```
	- #### Buying a product - that's user action and it should be caused by button `onCLick` event for example
- ### Separate Effects from Events (reactive and non-reactive logic)
- ### Use [[useEffectEvent|EffectEvent]]
- ### Only use dependecies that are really needed and used by the Effect
- ### Apply [[Single Responsibility Principle]] to Effects
- ### Use custom hooks to share stateful logic (not states itself) between components