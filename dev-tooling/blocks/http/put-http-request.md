---
description: Send HTTP PUT requests
---

# Put HTTP Request

### **Overview**

Within the GraphLinq Integrated Development Environment (IDE), the `Put HTTP Request` block is essential for initiating HTTP PUT requests to external web servers or APIs. This method is crucial for updating or replacing resources on a server, allowing developers to effectively modify existing records or refresh data on remote servers using RESTful APIs.

### **Block Characteristics**

* **Type**: Non-executive, operating without yellow connectors and is triggered indirectly as other blocks in the graph require its output.
* **Functionality**: Specially designed for data updates or replacements, making it an invaluable asset for interfacing with external APIs.

### **Inputs**

To execute a PUT request, the block necessitates the following inputs:

* **URL**: Points to the specific server or API endpoint where the data update or replacement will occur.
* **Headers**: An [Array](../array/) of [Key-Value](../base-variable/keyvalue.md) pairs, allowing for the transmission of additional request information or authentication details to the server. These headers are optional but can be pivotal for specific server communications.
* **Body**: Contains the payload with the data meant to be updated or replaced, often formatted as a JSON object or according to the API's prescribed data formats.

### **Output**

The block yields the server's response following the PUT request, encompassing the status code, any returned data, and potentially other relevant feedback.

### **Practical Application**

Imagine a scenario where the `Put HTTP Request` block updates user profile data through a fictional API:

1. The process begins with an interface (e.g., a web form or chatbot) that collects the user's new profile information.
2. This updated data is then stored within a designated variable or data store in the graph.
3. Subsequently, the block is configured with the API's URL, incorporating the updated profile data into the request body.
4. Headers are crucial at this stage; developers can append custom key-value pairs to convey specific instructions or authentication details to the server.
5. The block is indirectly activated by the graph's logic whenever its output becomes necessary.
6. The PUT request is dispatched to the API, aiming to update the user's profile on the server.
7. Following the request processing, the server returns a response, which might confirm the update or provide additional information.

This use case illustrates how the `Put HTTP Request` block seamlessly integrates data update capabilities into graphs, enabling interactions with a variety of web services and APIs that accept the HTTP PUT method. This enriches applications by allowing secure and efficient data modification or replacement on remote servers, thus offering users enhanced control over their data within the application ecosystem.
