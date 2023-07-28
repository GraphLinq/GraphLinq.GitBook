# Merge JSON

The Merge JSON block in the GraphLinq IDE serves as a powerful tool to combine multiple JSON objects into a single JSON object. JSON (JavaScript Object Notation) is a lightweight data interchange format used to represent data as key-value pairs, making it easy to read and process. The Merge JSON block enables developers to merge JSON data from different sources or manipulate and aggregate JSON objects within the graph.

_Block Inputs:_ The Merge JSON block has multiple inputs, each representing a JSON object. You can connect different blocks or APIs that produce JSON objects to these inputs. The block will combine the JSON objects from all the inputs into one cohesive JSON object.

_Block Output:_ The Merge JSON block outputs a single JSON object, which is the result of merging the JSON objects from all the connected inputs.

_Usage:_ The Merge JSON block is especially useful when developers need to combine JSON data from multiple sources or when they want to aggregate data into a single JSON object for further processing. It enables the seamless integration of JSON objects produced by various parts of the graph, facilitating unified data management and manipulation.

_Example:_ Suppose a graph fetches data from two different APIs, and each API returns data in JSON format. The task is to merge the data from both APIs into a single JSON object for further analysis. The Merge JSON block can be utilized to combine the JSON objects obtained from the two APIs:

**API 1 Output (JSON):**

```json
{
  "name": "John Doe",
  "age": 35,
  "email": "john.doe@example.com"
}
```

**API 2 Output (JSON):**

```json
{
  "address": "123 Main Street",
  "city": "New York",
  "country": "USA"
}
```

The Merge JSON block will merge the data from API 1 and API 2 into one JSON object:

**Merged JSON Output:**

```json
{
  "name": "John Doe",
  "age": 35,
  "email": "john.doe@example.com",
  "address": "123 Main Street",
  "city": "New York",
  "country": "USA"
}
```

_Note:_ When merging JSON objects, it is essential to ensure that the keys in the JSON objects do not conflict. If there are duplicate keys in the input JSON objects, the values from the last input will overwrite the values from the previous inputs.

The Merge JSON block empowers developers to efficiently combine JSON data from various sources or merge JSON objects produced within the graph. This consolidation of JSON objects enables streamlined data management and facilitates further data processing and analysis in complex applications and workflows.
