# Add JSON Property

The Add JSON Property block in the GraphLinq IDE serves as a valuable tool for dynamically adding properties to JSON objects. JSON (JavaScript Object Notation) is a widely used data interchange format that represents data as a collection of key-value pairs. With the Add JSON Property block, developers can enhance the flexibility and dynamic nature of their JSON objects by inserting new properties with corresponding values.

The Add JSON Property block takes two inputs:

1. JSON Object: This input represents the original JSON object to which a new property will be added.
2. Property Name: This input specifies the name of the property to be added to the JSON object.

The block's output is a new JSON object that includes the additional property specified by the input.

### Use Case

The Add JSON Property block is particularly useful when developers need to adapt their JSON objects based on dynamic or changing conditions. For instance, in an e-commerce application, the JSON object representing a shopping cart may need to be updated with a new product and its corresponding quantity. The Add JSON Property block can be employed to insert the product name as a property and its quantity as the associated value.

### Example

Let's consider an example where a graph receives a JSON object representing a user profile with existing properties such as "name," "age," and "email." At a later stage, the graph needs to add a new property, "location," to the user profile based on user input. The Add JSON Property block can be utilized to achieve this dynamically.

Suppose the initial JSON object is as follows:

```json
{
  "name": "John Doe",
  "age": 30,
  "email": "john@example.com"
}
```

With the Add JSON Property block, the graph can take the input JSON object and the new property name "location," along with its value, and create an updated JSON object:

```json
{
  "name": "John Doe",
  "age": 30,
  "email": "john@example.com",
  "location": "New York"
}
```

In this example, the Add JSON Property block dynamically added the "location" property with the value "New York" to the original JSON object.

_Note:_ When using the Add JSON Property block, it is crucial to ensure that the JSON object provided as input is valid. Any discrepancies in the input format may result in errors during the process of adding properties.

The Add JSON Property block empowers developers to build dynamic and adaptable JSON objects by allowing them to incorporate new properties on the fly. By doing so, developers can create more responsive and customizable graphs that cater to various scenarios and evolving data requirements.
