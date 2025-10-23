```jsx
const [state, setState] = useState(initialValue);
```
## The state is saved for the component it is written in
## It is possible to create multiple states
```jsx
const [stateOne, setStateOne] = useState(0);
const [stateTwo, setStateTwo] = useState("hello");
```
## To update the state
```jsx
setState(newValue);
setStateTwo("Hello new Hello");
```