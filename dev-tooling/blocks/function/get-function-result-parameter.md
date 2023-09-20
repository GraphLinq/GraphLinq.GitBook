# Get Function Result Parameter

Retrieve a specific parameter from the function's result set The "Get Function Result Parameter" node is a pivotal node within the GraphLinq IDE, allowing developers to access individual parameters from the result set of a function. By providing the means to isolate specific results, it facilitates more granular control over the data output, aiding in the development of complex, multi-faceted functionalities.

**Block Description**

Located under the Function category in the GraphLinq IDE, the "Get Function Result Parameter" node stands as a specialized tool for extracting distinct parameters from a function’s result set. It acts as a targeted retrieval system, pinpointing and delivering specified result parameters for further utilization within the graph.

**Input Parameters**

The node calls for the identification and input of two main parameters:

* **Results**: This input houses the full result set from which a specific parameter’s value will be retrieved.
* **Name**: Here, you specify the exact name of the parameter that you wish to extract from the function’s result set.

**Output**

This node provides a singular output:

* **Value**: After the execution, this output parameter will hold the value of the targeted result parameter, ready to be leveraged in subsequent nodes for further operations or analyses.

**Example Use Case**

Understanding the utility of the "Get Function Result Parameter" node is enhanced through its application in a practical scenario such as user account verification:

1. Consider a previously defined function that performs user account verification and returns a result set containing parameters like "verificationStatus" and "userDetails".
2. Following the function call, the "Get Function Result Parameter" node is implemented to isolate the "verificationStatus" parameter from the function’s result set.
3. In the "Name" input parameter of the node, "verificationStatus" is specified, targeting it for retrieval.
4. Upon execution, the node accesses the function’s result set and extracts the value of "verificationStatus".
5. The "Value" output parameter is then populated with the "verificationStatus" value, making it available for further processes such as conditionally directing the graph flow based on the verification status.

By deploying the "Get Function Result Parameter" node, developers can fine-tune the handling of function results, extracting and utilizing individual parameters to create flexible, adaptable, and advanced graph architectures, thereby elevating the potential and functionality of their developments.
