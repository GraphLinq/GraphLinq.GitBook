# On WebSocket Client Disconnect

The On WebSocket Client Disconnect block in the GraphLinq IDE allows developers to define actions and behaviors that should occur when a WebSocket client connection is closed or disconnected. WebSocket is a bidirectional communication protocol that enables real-time data exchange between clients and servers over a single, long-lived connection. However, WebSocket connections can be terminated or disconnected due to various reasons, such as network issues, server-side actions, or deliberate client disconnections.

The On WebSocket Client Disconnect block is essential for handling and responding to WebSocket disconnections and defining the subsequent course of action in the graph. When a WebSocket client is disconnected, this block triggers the specified actions based on the chosen disconnection reason or event.

The On WebSocket Client Disconnect block has several key input parameters:

1. WebSocket Client: The WebSocket Client input parameter is where developers connect the WebSocket client that they want to monitor for disconnections. This input links the block to the WebSocket client connector block responsible for establishing the WebSocket connection.
2. Disconnection Reason: The Disconnection Reason input parameter allows developers to select the specific reason or event that triggered the WebSocket client disconnection. The available options may include normal closure, abnormal closure, timeout, server-initiated disconnection, or client-initiated disconnection.
3. Auto Reconnect: The Auto Reconnect input parameter determines whether the WebSocket client should automatically attempt to reconnect after the disconnection occurs. Enabling this option allows the client to make subsequent connection attempts automatically, ensuring continuous operation even after temporary disconnections.

The On WebSocket Client Disconnect block also provides essential output parameters:

1. WebSocket Client: The WebSocket Client output parameter provides the disconnected WebSocket client, which can be used as an input for other blocks or actions that require the WebSocket client's reference or information.
2. Connection Status: The Connection Status output parameter indicates the current status of the WebSocket client connection. It helps developers track the connection state, especially when auto-reconnect is enabled, to identify the client's reconnection attempts.

By utilizing the On WebSocket Client Disconnect block, developers can implement robust error handling and recovery mechanisms for WebSocket connections. This block enables developers to define custom actions, such as logging disconnection events, sending notifications, or initiating reconnect strategies based on the disconnection reason. Properly handling WebSocket disconnections is crucial for ensuring the stability, reliability, and responsiveness of WebSocket-based applications that rely on real-time communication and data exchange.
