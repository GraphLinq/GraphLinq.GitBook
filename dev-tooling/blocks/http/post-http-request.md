---
description: Send HTTP POST requests
---

# Post HTTP Request

### **Overview**

The `Post HTTP Request` block in the GraphLinq Integrated Development Environment (IDE) is a fundamental tool for executing HTTP POST requests to external web servers or APIs. Utilizing the POST method, this block is designed to submit data for processing to a targeted resource on a server. It is an essential block for developers looking to create, update records, or send user inputs to remote endpoints via RESTful APIs.

### **Block Characteristics**

* **Type**: Non-executive
* **Connectivity**: Lacks yellow connectors; activated indirectly by the demand for its output in graph flows
* **Functionality**: Facilitates the submission of data to external servers or APIs, supporting a wide range of interactions.

### **Inputs**

To execute an HTTP POST request, the `Post HTTP Request` block requires:

* **URL**: Identifies the API endpoint or server resource where the data will be processed.
* **Headers**: An [Array](../array/) of [Key-Value](../base-variable/keyvalue.md) pairs, allowing for the transmission of additional request information or authentication details to the server. These headers are optional but can be pivotal for specific server communications.
* **Body**: The main content of the POST request, containing the data intended for submission. This is often structured as a JSON object or in another format suitable for the target API.

### **Output**

The output from the block includes the server's response to the POST request, which might comprise the status code, returned data, or other pertinent feedback from the server.

### **Practical Application**

Imagine a scenario where the `Post HTTP Request` block is used to send user feedback to a hypothetical API. The process involves:

1. Gathering feedback through a user interface, such as a web form or chat interface.
2. Storing the collected feedback in a graph variable or data source.
3. Configuring the block with the API's URL and incorporating the feedback within the request body.
4. Optionally adding custom headers for additional request specifications or authentication.
5. The block is invoked indirectly as needed by the graph's flow for its output.
6. Upon execution, it sends the POST request to the API, delivering the user feedback for storage.
7. The API processes the submission and responds, potentially with confirmation of receipt or additional information.

This example highlights the `Post HTTP Request` block's role in enabling graphs to incorporate data submission functionalities seamlessly. With this block, developers can extend their applications to interact dynamically with web services and APIs supporting the HTTP POST method, thereby enriching the applications' interactivity and capabilities in handling user inputs or other data transactions remotely.
