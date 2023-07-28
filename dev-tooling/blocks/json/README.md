# JSON

**JSON Blocks**

JSON (JavaScript Object Notation) Blocks in the GraphLinq IDE facilitate the manipulation and transformation of data in the JSON format. JSON is a widely used lightweight data interchange format, designed to be both human-readable and machine-parsable. It serves as a standard data format for transmitting and storing structured data between servers and web applications.

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

The JSON Blocks available are: [`Last Node to JSON`](last-node-to-json.md), [`Convert To JSON`](convert-to-json.md), [`Add JSON Property`](add-json-property.md), [`Create JSON Object`](create-json-object.md), [`JSON Deserialize To Array`](json-deserialize-to-array.md), [`JSON to JSON Object`](json-to-json-object.md), [`Merge JSON`](merge-json.md), [`Serialize JSON Object`](serialize-json-object.md), and [`Serialize to JSON`](serialize-to-json.md).
