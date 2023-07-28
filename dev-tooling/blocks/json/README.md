# JSON

JSON (JavaScript Object Notation) is a fundamental category of blocks in the GraphLinq IDE, designed to work with JSON data. JSON is a lightweight data interchange format widely used to transmit and store structured data between servers and web applications. Its simplicity, human-readability, and compatibility with various programming languages make it a popular choice for data representation.

JSON blocks facilitate the manipulation and transformation of JSON data, allowing developers to create dynamic and interactive graphs that can handle complex data structures effectively.

The JSON category encompasses a variety of blocks, each serving a specific purpose in working with JSON data. Let's explore the subcategories and their respective blocks:

The [Last Node To JSON](last-node-to-json.md) block is used to convert the output of the previous block in the graph to JSON format. This allows developers to take the data produced by earlier blocks and represent it in the JSON structure.

The [Convert To JSON](convert-to-json.md) block is a versatile component that takes input values and converts them into JSON format. It enables developers to create custom JSON objects and arrays from various data types, including strings, integers, decimals, and more.

The [Add JSON Property](add-json-property.md) block is used to add a new property to an existing JSON object. Developers can specify the property name and its corresponding value, dynamically expanding the JSON object as needed.

The [Create JSON Object](create-json-object.md) block allows developers to build a JSON object from scratch. By adding multiple properties and their corresponding values, developers can construct complex JSON structures tailored to their application's requirements.

The [JSON Deserialize To Array](json-deserialize-to-array.md) block is essential for transforming a JSON array (represented as a string) back into a structured array within the graph. This allows developers to extract and work with specific elements of the JSON array as needed.

The [JSON To JSON Object](json-to-json-object.md) block converts a JSON string into a JSON object representation. This is useful for parsing and manipulating JSON data obtained from external sources or APIs.

The [Merge JSON](merge-json.md) block allows developers to merge two or more JSON objects into a single JSON object. This facilitates data aggregation and combination, enabling developers to consolidate multiple sets of data.

The [Serialize JSON Object](serialize-json-object.md) block performs the opposite operation of JSON To JSON Object. It converts a JSON object into a JSON string, making it suitable for external data exchange and storage.

The [Serialize To JSON](serialize-to-json.md) block converts various data types (such as strings, numbers, arrays) into a JSON string. This is particularly useful when preparing data to be sent to APIs or stored in JSON-based databases.

The JSON category offers a comprehensive suite of blocks to work with JSON data effectively. Whether it's converting data to or from JSON format, merging JSON objects, or creating custom JSON structures, these blocks provide the necessary tools to handle JSON data with precision and flexibility. JSON manipulation is essential in modern web applications, and these blocks enable developers to create sophisticated and interactive graphs that interact seamlessly with JSON-based APIs and services.



***

### More Information

JSON data is organized as a collection of key/value pairs, where keys are always represented as strings, and values can be strings, numbers, arrays, or other JSON objects. JSON Blocks enable developers to work with this data format seamlessly, allowing them to extract, modify, and generate JSON data as part of their graph's logic.

The available JSON Blocks cover a wide range of functionalities, from converting data to and from JSON format to merging, deserializing, and serializing JSON objects. With these blocks, developers can perform complex JSON-related operations, such as adding properties, creating JSON objects, and transforming JSON data to meet the requirements of their applications.

By harnessing the power of JSON Blocks, developers can efficiently work with JSON data, enabling the integration of external APIs, data serialization, and data interchange in their GraphLinq graphs. These blocks play a crucial role in ensuring seamless communication and data manipulation within the graph, contributing to the development of robust and versatile applications.

{% code title="JSON Example" lineNumbers="true" %}
```json
{
  "name": "GraphLinq Protocol",
  "allTimeHighUSD": 0.10966683966210045,
  "rate": 0.01375348745855626,
  "volume": 913981,
  "cap": 4676184,
  "liquidity": 36833,
  "delta": {
    "hour": 1.0242,
    "day": 0.9969,
    "week": 1.1052,
  }
}
```
{% endcode %}

