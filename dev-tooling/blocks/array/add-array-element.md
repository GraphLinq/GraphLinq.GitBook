# Add Array Element

The "Add Array Element" block in the GraphLinq IDE is a powerful tool for dynamically expanding arrays by adding new elements. This block is instrumental in scenarios where ongoing data collection or real-time data updates are necessary.

### **Block Description**

The "Add Array Element" block falls under the Array category in the GraphLinq IDE. It's designed to insert a new element into an existing array, with optional size limitation functionalities.

### **Input Parameters**

* **Array (List):** The array to which a new element will be added. It must be an existing array.
* **Element (object):** The new element to be added to the array. It can be of any data type.
* **Size Limit (int):** An optional parameter that specifies the maximum allowed size of the array. If provided, the array will not exceed this size.

### **Output**

This block does not have an explicit output but modifies the input array by adding the new element.

### **Example Use Case**

Consider a scenario where real-time stock market data is collected. As new stock prices arrive, the "Add Array Element" block can add these prices to an existing array for later analysis or visualization.
