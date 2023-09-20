# Get Function Parameter

Extract a parameter value from the current function context

The "Get Function Parameter" node is a foundational tool within the GraphLinq IDE, serving to extract specific parameters from the existing function context during graph execution. This node facilitates streamlined parameter management, promoting efficient and dynamic graph constructions.

**Block Description**

The "Get Function Parameter" node resides in the Function category of the GraphLinq IDE. Designed to access and retrieve a specified parameter within the ongoing function context, this node is instrumental in shaping adaptive and intelligent graph functionalities. As a non-executive node, it doesn't entail direct execution but operates implicitly to furnish the desired parameter value whenever invoked by subsequent nodes.

**Input Parameters**

This node demands the specification of a single input parameter:

* **Name**: This parameter is where you denote the name of the parameter you wish to extract from the current function context. The defined name should match exactly with one of the parameters in the function's context.

**Output**

Upon its invocation, the node produces the following output:

* **Value**: Post the computation, this output parameter holds the retrieved value of the specified function parameter, poised for further manipulations or utilities in the nodes downstream.

**Example Use Case**

To elucidate the "Get Function Parameter" node's operation, let’s delve into a use case involving a user authentication function:

1. A function is constituted to authenticate user credentials, wherein it accepts parameters such as "username" and "password".
2. As the graph runs, different segments of the function utilize the "Get Function Parameter" node to fetch the "username" and "password" parameters separately.
3. In each "Get Function Parameter" node, the respective parameter name is specified in the "Name" input parameter, directing the node to retrieve the correct value from the function context.
4. Following the retrieval, the "Value" output parameter of each node becomes populated with the respective parameter values.
5. These extracted values then undergo further processes such as validation checks, database verifications, etc., guided by the subsequent nodes in the graph.

By harnessing the "Get Function Parameter" node, developers can foster a nuanced parameter management system, drawing out individual parameters seamlessly for specific functions and analyses. This node thus plays a pivotal role in building intricate and efficient graph setups, enhancing the overall dynamism and adaptability of applications developed through the GraphLiq IDE.
