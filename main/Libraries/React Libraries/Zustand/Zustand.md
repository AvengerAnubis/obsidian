## A state management library for [[React]] which API is based on [[Hook|hooks]]
## First, create a store
```tsx
import { create } from 'zustand';
const useBear = create((set) => ({ 
	bears: 0, 
	increasePopulation: () => set((state) => ({ bears: state.bears + 1 })),
	removeAllBears: () => set({ bears: 0 }),
	updateBears: (newBears) => set({ bears: newBears }), 
}))
```
## Second, bind your component
```tsx
function BearCounter() {
	const bears = useBear((state) => state.bears)
	return <h1>{bears} bears around here...</h1>
}

function Controls() {
	const increasePopulation = useBear((state) => state.increasePopulation)
	return <button onClick={increasePopulation}>one up</button>
}

```
