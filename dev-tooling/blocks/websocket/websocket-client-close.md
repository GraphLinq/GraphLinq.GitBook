# WebSocket Client Close

The WebSocket Client Close block in the GraphLinq IDE is a powerful tool for gracefully closing WebSocket connections. When working with WebSocket communications, it is essential to manage and handle the closure of connections properly. The WebSocket Client Close block allows developers to initiate the process of closing a WebSocket connection in a controlled manner.

The WebSocket Client Close block has two main input parameters:

1. WebSocket Client: This input parameter specifies the WebSocket client connection that needs to be closed. Developers can connect this input to a WebSocket client connector block or any other block that outputs a WebSocket client connection.
2. Code: The code input parameter allows developers to specify a numeric code that represents the reason for closing the WebSocket connection. WebSocket protocol defines various numeric codes to indicate different types of closure reasons, such as normal closure, abnormal closure, and custom codes for application-specific purposes.

Additionally, the WebSocket Client Close block has an optional input parameter:

3. Reason: The reason input parameter is an optional text field that developers can use to provide additional details or explanations for the closure of the WebSocket connection. This parameter is useful for including human-readable descriptions of the closure reason, especially when using custom closure codes.

When the WebSocket Client Close block is executed, it sends a close frame to the WebSocket server, initiating the process of closing the connection. The WebSocket server responds to this request, and both the client and server perform the necessary cleanup operations before the connection is fully closed.

Using the WebSocket Client Close block, developers can ensure that WebSocket connections are terminated gracefully, avoiding abrupt disconnections and allowing both clients and servers to handle the closure process smoothly. Proper management of WebSocket connections is crucial for building reliable and robust real-time communication applications that provide seamless user experiences and efficient data exchange between clients and servers.
