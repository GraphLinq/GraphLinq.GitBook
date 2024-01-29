---
description: Send HTTP GET requests
---

# Get HTTP Request

### **Overview**

The `Get HTTP Request` block within the GraphLinq Integrated Development Environment (IDE) stands as a pivotal component for executing HTTP GET requests towards external web servers or APIs. Employing the GET method, a fundamental HTTP protocol, this block requests data from a designated resource on a server. It serves as a key instrument for developers to fetch data from RESTful APIs, enhancing their capability to access diverse data forms from remote endpoints.

### **Block Characteristics**

* **Type**: Non-executive
* **Connectivity**: No yellow connectors; indirectly activated through output demand in graph execution
* **Functionality**: Facilitates data retrieval by integrating with external servers or APIs

### **Inputs**

The functionality of the `Get HTTP Request` block is driven by several crucial inputs:

* **URL**: Specifies the endpoint or resource on the web server from which data is to be retrieved.
* **Headers**: An [Array](../array/) of [Key-Value](../base-variable/keyvalue.md) pairs, allowing for the transmission of additional request information or authentication details to the server. These headers are optional but can be pivotal for specific server communications.
* **Query Parameters**: These parameters are appended to the URL, enabling the passage of supplementary information or criteria for the data request.

### **Output**

Upon execution, the block outputs the server's response to the HTTP GET request. This output encompasses the response status code and data, alongside other pertinent server-returned information.

### **Practical Application**

Consider a scenario where the `Get HTTP Request` block is employed to access a fictional weather data API. The process unfolds as follows:

1. The graph initializes by acquiring a location (e.g., city or geographical coordinates) from an input source or variable.
2. The block is configured with the API's URL, incorporating the location into the resource path or as part of the query parameters.
3. Optionally, developers may append custom headers to the request for authentication or tailored server interactions.
4. The block is indirectly invoked as subsequent blocks in the graph necessitate its output.
5. The GET request is dispatched to the weather API, soliciting current weather data for the defined location.
6. The server processes this request and responds with the relevant weather information for the given location.

This example underscores the `Get HTTP Request` block's utility in integrating real-time data retrieval into GraphLinq graphs. By leveraging this block, developers can enhance their applications with dynamic data from various web services and APIs, enriching user experiences with up-to-date information from external sources.
