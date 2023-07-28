---
description: Convert arrays into JSON format
---

# Array To JSON Body

The Array To JSON Body block is a valuable component in the GraphLinq IDE that facilitates the conversion of arrays into JSON format. JSON (JavaScript Object Notation) is a widely used data interchange format, and it is particularly useful for representing complex data structures, such as arrays and objects, in a human-readable and easy-to-parse format.

### Block Description

The Array To JSON Body block is categorized under the HTTP blocks in the GraphLinq IDE. It serves as a non-executive block, meaning it does not have any yellow connectors and is implicitly called whenever its output is required by another block during graph execution.

### Input Parameters

The Array To JSON Body block requires one primary input parameter:

1. Array: The array input contains the data elements that need to be converted into JSON format. This array can consist of various data types, including strings, numbers, booleans, and even other arrays or objects.

### Output

The Array To JSON Body block outputs the JSON representation of the input array. This JSON output can be used as the body of an HTTP request when interacting with APIs that expect data in JSON format.

### Example Use Case

Let's explore a practical example where the Array To JSON Body block is utilized in a graph that interacts with an online store's API to place an order for multiple items.

1. The graph receives inputs from a user interface or data source containing the details of the items the user wants to purchase. These item details are stored in an array within the graph.
2. The Array To JSON Body block is then called, taking the array of item details as input.
3. The block automatically converts the array into JSON format, maintaining the data's structure and type information.
4. The JSON output is used as the body of an HTTP POST request to the online store's API.
5. The API processes the request and places the order for the items specified in the JSON body.
6. The API responds with a confirmation or order status, which can be further processed by other blocks in the graph.

By leveraging the Array To JSON Body block, developers can effortlessly convert arrays containing structured data into JSON format, enabling seamless interactions with APIs that require JSON-formatted data. This capability allows developers to build applications that efficiently communicate with various web services and APIs, streamlining data exchange processes and enhancing the overall functionality of their applications.
