# Last Node to JSON

The Last Node To JSON block is a powerful tool in the GraphLinq IDE that allows developers to convert the output of the previous node in the graph into JSON format. This block is particularly useful when developers want to represent the data generated by earlier blocks as a structured JSON object.

The Last Node To JSON block does not require any specific input. Instead, it automatically takes the output of the previous node in the graph as its input. This feature makes it incredibly convenient as developers don't need to manually provide input; the block implicitly receives the data from the previous node.

The block's output is a JSON representation of the data received from the previous node. The output is a JSON object that can include nested properties and values, making it versatile for handling complex data structures.



### Use Case

Consider a scenario where a graph fetches real-time cryptocurrency data from an API using the HTTP blocks. The data obtained might include details like the current price, volume, and market cap of a particular cryptocurrency. The Last Node To JSON block can then be used to convert this data into a JSON object, making it easier to process and display on a user interface or send to other external services.

### Example

Let's take a simplified example where a graph calculates the sum of two numbers, A and B, using the Add A + B block. The result of this addition is then passed to the Last Node To JSON block. The JSON output will be a representation of the sum in the following format:

```json
{
  "result": 10
}
```

In this example, the "result" property is automatically generated by the Last Node To JSON block, and its value is the sum of numbers A and B.

_Note:_ It's important to ensure that the data provided to the Last Node To JSON block is in a suitable format for JSON representation. For example, non-JSON-compatible data, such as circular structures, might cause errors in the process. Developers should ensure that the output of the previous node is compatible with JSON formatting to achieve accurate results.

The Last Node To JSON block simplifies the process of converting graph data into JSON format, making it easier to work with and transmit structured data between different parts of the graph or to external systems. Its implicit input mechanism ensures seamless integration with other blocks, enhancing the overall efficiency and flexibility of the graph.
