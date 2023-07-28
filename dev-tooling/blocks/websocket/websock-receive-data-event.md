# WebSock Receive Data Event

The WebSocket Receive Data Event block in the GraphLinq IDE is a powerful tool that enables developers to capture and process data received from a WebSocket client. WebSocket is a bidirectional communication protocol that allows real-time data exchange between clients and servers over a single, long-lived connection. When clients send data to the server via the WebSocket connection, the WebSocket Receive Data Event block can capture and process this incoming data for further actions or computations within the graph.

The WebSocket Receive Data Event block plays a crucial role in creating interactive and responsive applications that rely on real-time data updates from WebSocket clients. It allows developers to define how the graph should react to incoming data, enabling the implementation of various real-time features such as chat applications, live data feeds, and interactive web interfaces.

The WebSocket Receive Data Event block has the following key input parameters:

1. WebSocket Client: The WebSocket Client input parameter is where developers connect the WebSocket client that they want to monitor for incoming data. This input links the block to the WebSocket client connector block responsible for establishing the WebSocket connection.
2. Data Handler: The Data Handler input parameter is where developers define the logic and actions that should be performed when data is received from the WebSocket client. The Data Handler can be a custom function or a sequence of blocks that process and utilize the incoming data as needed.

The WebSocket Receive Data Event block also provides the following essential output parameters:

1. WebSocket Client: The WebSocket Client output parameter provides the WebSocket client reference, which can be used as an input for other blocks or actions that require the WebSocket client's reference or information.
2. Data: The Data output parameter contains the data received from the WebSocket client. This data can be in various formats, such as strings, JSON objects, binary data, etc., depending on the nature of the data sent by the client.

The WebSocket Receive Data Event block empowers developers to create dynamic and interactive applications that can respond in real-time to user inputs or external data updates. By leveraging the Data Handler input, developers can customize how the graph processes and utilizes the incoming data, allowing for a wide range of possibilities in WebSocket-based applications. Whether it's updating a live chat feed, visualizing real-time data, or triggering specific actions based on incoming data, the WebSocket Receive Data Event block is an essential tool for building responsive and engaging applications.
