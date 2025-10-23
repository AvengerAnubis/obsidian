## Extracts non-reactive logic outside of the event
```jsx
import { useEffect, useEffectEvent } from 'react';  

function ChatRoom({ roomId, theme }) {  
	const onConnected = useEffectEvent(() => {  
		showNotification('Connected!', theme);  
	});
	useEffect(() => {  
		const connection = createConnection(serverUrl, roomId);  
			connection.on('connected', () => {  
			onConnected();  
		});  
		connection.connect();  
		return () => connection.disconnect();  
	}, [roomId]); // ✅ All dependencies declared
	//...
}
```