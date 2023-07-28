---
description: Send HTTP POST requests
---

# Post HTTP Request

The Post HTTP Request block is a crucial component in the GraphLinq IDE that enables sending HTTP POST requests to external web servers or APIs. The POST method is one of the standard HTTP methods used to submit data to be processed to a specified resource on the server. This block empowers developers to interact with RESTful APIs and perform various actions, such as creating new records, updating data, or submitting user inputs to remote servers.

Block Description:

### Block Description

Similar to other HTTP request blocks, the Post HTTP Request block is a non-executive block, meaning it does not have any yellow connectors and is implicitly called whenever its output is required by another block during graph execution. This versatility makes it a powerful tool for handling data submission and interaction with external APIs.

Input Parameters:

### Input Parameters

The Post HTTP Request block requires several input parameters to perform the HTTP POST request:

1. URL (Uniform Resource Locator): The URL of the web server or API endpoint to which the POST request will be sent. This parameter specifies the resource that will process the submitted data.
2. Headers: Headers are optional parameters that provide additional information to the server about the request. Developers can include custom headers as key-value pairs to communicate specific requirements or authentication details to the server.
3. Body: The body of the POST request contains the data to be submitted to the server. This data is typically formatted as a JSON object or other data formats, depending on the API's requirements.

### Output

The Post HTTP Request block outputs the result of the HTTP POST request. This result may include the response status code, response data, or any other relevant information returned by the server.

### Example Use Case

Let's consider a practical example where the Post HTTP Request block is used to interact with a fictional API that allows users to submit feedback messages. In this scenario, the graph needs to collect user inputs and send them to the API to store the feedback messages.

1. The graph starts with a user interface (e.g., web form or chatbot) that collects the user's feedback message.
2. The user's feedback message is stored in a variable or data source within the graph.
3. The Post HTTP Request block is then configured with the API's URL, including the user's feedback message as part of the request body.
4. Optionally, custom headers can be added to the request for authentication or other purposes.
5. The Post HTTP Request block is implicitly called when its output is required by another block in the graph.
6. Upon execution, the block sends the HTTP POST request to the API, submitting the user's feedback message to be stored on the server.
7. The server processes the request and returns the response, which may include a success status or other relevant data.

By utilizing the Post HTTP Request block, developers can seamlessly integrate data submission functionality into their graphs, allowing them to interact with various web services and APIs that support the HTTP POST method. This empowers them to build powerful applications that can securely submit and process user inputs or perform other data-related actions on remote servers, enhancing the functionality and interactivity of their applications.
