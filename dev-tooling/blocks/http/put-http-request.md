---
description: Send HTTP PUT requests
---

# Put HTTP Request

The Put HTTP Request block is a fundamental component in the GraphLinq IDE that enables sending HTTP PUT requests to external web servers or APIs. The PUT method is one of the standard HTTP methods used to update or replace a resource on the server. This block empowers developers to interact with RESTful APIs and perform various actions, such as modifying existing records or updating data on remote servers.

### Block Description

Similar to other HTTP request blocks, the Put HTTP Request block is a non-executive block, meaning it does not have any yellow connectors and is implicitly called whenever its output is required by another block during graph execution. This versatility makes it a powerful tool for handling data updates and interactions with external APIs.

### Input Parameters

The Put HTTP Request block requires several input parameters to perform the HTTP PUT request:

1. URL (Uniform Resource Locator): The URL of the web server or API endpoint to which the PUT request will be sent. This parameter specifies the resource that will be updated or replaced on the server.
2. Headers: Headers are optional parameters that provide additional information to the server about the request. Developers can include custom headers as key-value pairs to communicate specific requirements or authentication details to the server.
3. Body: The body of the PUT request contains the data to be updated or replaced on the server. This data is typically formatted as a JSON object or other data formats, depending on the API's requirements.

### Output

The Put HTTP Request block outputs the result of the HTTP PUT request. This result may include the response status code, response data, or any other relevant information returned by the server.

### Example Use Case

Let's consider a practical example where the Put HTTP Request block is used to interact with a fictional API that allows users to update their profile information. In this scenario, the graph needs to collect updated user profile data and send it to the API to update the user's profile on the server.

1. The graph starts with a user interface (e.g., web form or chatbot) that collects the updated profile data.
2. The updated profile data is stored in a variable or data source within the graph.
3. The Put HTTP Request block is then configured with the API's URL, including the updated profile data as part of the request body.
4. Optionally, custom headers can be added to the request for authentication or other purposes.
5. The Put HTTP Request block is implicitly called when its output is required by another block in the graph.
6. Upon execution, the block sends the HTTP PUT request to the API, updating the user's profile data on the server.
7. The server processes the request and returns the response, which may include a success status or other relevant data.

By utilizing the Put HTTP Request block, developers can seamlessly integrate data update functionality into their graphs, allowing them to interact with various web services and APIs that support the HTTP PUT method. This empowers them to build powerful applications that can securely update or replace data on remote servers, providing users with the ability to manage and modify their information within the application's ecosystem.
