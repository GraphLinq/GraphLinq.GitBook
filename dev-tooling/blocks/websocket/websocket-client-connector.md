# WebSocket Client Connector

The WebSocket Client Connector block in the GraphLinq IDE serves as the entry point for establishing WebSocket connections with remote servers or services. WebSocket is a communication protocol that enables real-time bidirectional data transfer between clients and servers over a single, long-lived connection. The WebSocket Client Connector block empowers developers to create WebSocket clients and initiate connections to WebSocket servers, enabling real-time data exchange and interaction with external systems.

The WebSocket Client Connector block has several key input parameters:

1. URL: The URL input parameter is where developers specify the WebSocket server's address to which the client will connect. It typically starts with "ws://" for unsecured connections or "wss://" for secure connections (encrypted with SSL/TLS).
2. Headers: The Headers input parameter allows developers to include custom HTTP headers in the WebSocket client's handshake request. These headers can be used for authentication, passing tokens, or providing additional information to the WebSocket server.
3. Protocols: The Protocols input parameter is used to specify a list of subprotocols that the client can support. Subprotocols are specific application-level protocols built on top of the WebSocket protocol. The server can then choose to accept or reject the client's connection based on the supported protocols.
4. Auto Reconnect: The Auto Reconnect input parameter determines whether the WebSocket client should automatically attempt to reconnect to the server if the connection is lost unexpectedly. Enabling this option ensures that the client remains connected and operational even in cases of temporary disruptions.

The WebSocket Client Connector block also provides essential output parameters:

1. WebSocket Client: The WebSocket Client output parameter provides the established WebSocket client connection, which can be used as an input for other WebSocket-related blocks to send and receive data.
2. Connection Status: The Connection Status output parameter indicates the current status of the WebSocket client connection. It helps developers monitor the connection state and respond to changes or events, such as successful connections, disconnections, or connection errors.

By utilizing the WebSocket Client Connector block, developers can create robust WebSocket clients that seamlessly connect to remote servers and enable real-time data streaming and interaction. WebSocket technology is well-suited for various real-time applications, such as chat applications, financial trading platforms, gaming systems, and collaborative tools, where low-latency and bidirectional communication are critical for providing smooth and responsive user experiences.
