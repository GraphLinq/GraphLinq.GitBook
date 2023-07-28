---
description: Send HTTP GET requests
---

# Get HTTP Request

The Get HTTP Request block is a fundamental element in the GraphLinq IDE that enables sending HTTP GET requests to external web servers or APIs. The GET method is one of the standard HTTP methods used to request data from a specified resource on the server. This block empowers developers to interact with RESTful APIs and retrieve various types of data from remote servers.

### Block Description

The Get HTTP Request block is a non-executive block, meaning it does not have any yellow connectors and is not explicitly called by other blocks. Instead, it is implicitly called whenever its output is required as input by another block during graph execution. This makes it a versatile tool for handling data retrieval in graphs and allows developers to seamlessly integrate it into their applications.

### Input Parameters

The Get HTTP Request block requires several input parameters to perform the HTTP GET request:

1. URL (Uniform Resource Locator): The URL of the web server or API endpoint from which the GET request will fetch data. This parameter specifies the resource that contains the desired data.
2. Headers: Headers are optional parameters that provide additional information to the server about the request. Developers can include custom headers as key-value pairs to communicate specific requirements or authentication details to the server.
3. Query Parameters: Query parameters are used to pass additional data with the GET request. They are typically added to the URL and can be used for filtering or specifying certain conditions for data retrieval.

### Output

The Get HTTP Request block outputs the result of the HTTP GET request. This result may include the response status code, response data, or any other relevant information returned by the server.

### Example Use Case

Let's consider a practical example where the Get HTTP Request block is used to interact with a fictional API that provides weather data. In this scenario, the graph needs to fetch the current weather information for a specific location.

1. The graph starts by retrieving the location (e.g., city or coordinates) from a variable or data source.
2. The Get HTTP Request block is then configured with the API's URL, including the location as part of the resource path or query parameters.
3. Optionally, custom headers can be added to the request for authentication or other purposes.
4. The Get HTTP Request block is implicitly called when its output is required by another block in the graph.
5. Upon execution, the block sends the GET request to the API, requesting the weather data for the specified location.
6. The server processes the request and returns the response, which includes the current weather information for the specified location.

By utilizing the Get HTTP Request block, developers can seamlessly integrate data retrieval functionality into their graphs, allowing them to interact with various web services and APIs that support the HTTP GET method. This empowers them to build powerful applications that can fetch and display real-time data from remote servers, enhancing the functionality and user experience of their applications.
