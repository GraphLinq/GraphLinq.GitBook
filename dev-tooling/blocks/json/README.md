# JSON

JSON (JavaScript Object Notation) is a lightweight data interchange format used to transmit data between servers and web applications. It is easy for humans to read and write and easy for machines to parse and generate.

The data is represented as a collection of key/value pairs, with the keys always being strings and the values being one of several data types, including strings, numbers, arrays, or other JSON objects.

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
