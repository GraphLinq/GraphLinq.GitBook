---
description: Transform arrays into key-value pairs
---

# Array To Body Values

The Array To Body Values block is a powerful component within the GraphLinq IDE that facilitates the transformation of arrays into key-value pairs suitable for use as the body of an HTTP request. When interacting with APIs or web services, it is common to send data in the form of key-value pairs within the request body. The Array To Body Values block simplifies this process by converting arrays into a format that can be readily utilized as an HTTP request body.

### Block Description

The Array To Body Values block is categorized under the HTTP blocks in the GraphLinq IDE. As a non-executive block, it does not have any yellow connectors and is implicitly called whenever its output is required by another block during graph execution.

### Input Parameters

The Array To Body Values block requires one primary input parameter:

1. Array: The array input contains the data elements that need to be transformed into key-value pairs. This array can include various data types, such as strings, numbers, and booleans.

### Output

The Array To Body Values block outputs the data from the input array in the form of key-value pairs suitable for use as the body of an HTTP request. The keys represent the indices of the array elements, and the values represent the corresponding data elements.

### Example Use Case

Let's explore a practical example of how the Array To Body Values block can be utilized in a graph that interacts with an API to update user information.

1. The graph receives inputs from a user interface or data source containing the updated information for a user. This information is stored in an array within the graph.
2. The Array To Body Values block is then called, taking the array of user data as input.
3. The block automatically transforms the array data into key-value pairs, with each index of the array serving as the key and the corresponding data element as the value.
4. The resulting key-value pairs are used as the body of an HTTP PUT request to the API's endpoint for updating user information.
5. The API processes the request and updates the user's information based on the provided key-value pairs.
6. The API responds with a success message or status, which can be further processed by other blocks in the graph.

By leveraging the Array To Body Values block, developers can easily convert arrays into key-value pairs suitable for use in HTTP requests, simplifying the data transmission process when interacting with various APIs and web services. This capability enables developers to create robust applications that seamlessly exchange data with external services, enhancing the overall functionality and versatility of their applications.
