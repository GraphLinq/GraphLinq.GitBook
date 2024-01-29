---
description: Send HTTP DELETE requests
---

# Delete HTTP Request

The Delete HTTP Request block is an essential component in the GraphLinq IDE that facilitates sending HTTP DELETE requests to external web servers or APIs. The DELETE method is one of the standard HTTP methods used to request the removal of a specified resource on the server. This block empowers developers to interact with RESTful APIs and perform various operations that involve resource deletion.

### Block Description

The Delete HTTP Request block is a non-executive block, meaning it does not have any yellow connectors and is not explicitly called by other blocks. Instead, it is implicitly called whenever its output is required as input by another block during graph execution. This makes it a versatile tool for handling resource deletion in graphs and allows developers to seamlessly integrate it into their applications.

### Input Parameters

The Delete HTTP Request block requires several input parameters to perform the HTTP DELETE request:

1. URL (Uniform Resource Locator): The URL of the web server or API endpoint to which the DELETE request will be sent. This parameter specifies the resource that needs to be deleted.
2. Headers: An [Array](../array/) of [Key-Value](../base-variable/keyvalue.md) pairs, allowing for the transmission of additional request information or authentication details to the server. These headers are optional but can be pivotal for specific server communications.
3. Query Parameters: Query parameters are used to pass additional data with the DELETE request. They are typically added to the URL and can be used for filtering or specifying certain conditions for the resource deletion.

### Output

The Delete HTTP Request block outputs the result of the HTTP DELETE request. This result may include the response status code, response data, or any other relevant information returned by the server.

### Example Use Case

Let's consider a practical example where the Delete HTTP Request block is used to interact with a fictional API that manages user accounts. In this scenario, the graph needs to delete a specific user account based on the user's ID.

1. The graph starts by retrieving the user ID from a variable or data source.
2. The Delete HTTP Request block is then configured with the API's URL and the user ID as part of the resource path.
3. Optionally, custom headers can be added to the request for authentication or other purposes.
4. The Delete HTTP Request block is implicitly called when its output is required by another block in the graph.
5. Upon execution, the block sends the DELETE request to the API, requesting the deletion of the specified user account.
6. The server processes the request and returns the response, which may include a success status code to indicate a successful deletion.

By utilizing the Delete HTTP Request block, developers can seamlessly integrate resource deletion functionality into their graphs, allowing them to interact with various web services and APIs that support the HTTP DELETE method. This empowers them to build powerful applications that can perform CRUD (Create, Read, Update, Delete) operations and efficiently manage data on remote servers.
