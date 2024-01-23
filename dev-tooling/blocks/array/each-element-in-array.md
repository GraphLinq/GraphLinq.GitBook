# Each Element In Array

The "Each Element In Array" block in GraphLinq IDE iterates over each element in an array, providing a way to perform operations on individual array elements.

### Block Description

This block, under the Array category, is designed for element-wise processing within an array.

### Input Parameters

* Array (List\<object>): The array to be iterated over.

### Output Parameters

* Each (Node): Represents the node executed for each array element.
* Item (object): The current element being processed in the array.

### Example Use Case

In a customer feedback analysis graph, the "Each Element In Array" block can be used to iterate over each piece of feedback, processing it for sentiment analysis.

### Example

In this example we first create a new array and add two elements. (Item1 and Item2). Next we loop through the array and perform a print on each item. When complete, the graph prints DONE and stops the graph.

<figure><img src="../../../.gitbook/assets/Screenshot 2024-01-23 144634.png" alt=""><figcaption></figcaption></figure>
