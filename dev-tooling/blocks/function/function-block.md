# Function Block

Create a new function within the graph The Function block is a core component in the GraphLinq ecosystem, allowing developers to define reusable functions within their block graphs. These functions can accept parameters and return values, facilitating modular and organized development by grouping related operations into single function units, which can be called multiple times throughout a graph with different inputs.

**Block Description**

The Function block resides under the Function category in the GraphLinq IDE. This block initializes a new function context whenever it is executed, setting the stage for the operations defined within the function to be carried out. The function context holds necessary data like call parameters and return values, which are essential for the function’s operation.

**Input Parameters**

The Function block requires one primary input parameter:

* **Name**: This is a string parameter where you define the unique name for the function. This name is used when calling the function from other parts of the graph.

**Properties**

* **CallParameters**: A dictionary holding the parameters that will be passed when the function is called. It is manipulated through other nodes that interact with functions.
* **Context**: This property holds the function context created during the execution, storing the return values and call parameters for the current cycle of execution.

**Methods**

* **OnExecution**: This method creates a new function context and sets it as the current function context in the current cycle of the graph execution. It does not require any parameters and returns a boolean indicating the success of the operation.
* **GetFunctionInParameters**: This method dissects the required parameters for the function, returning a list of parameter names as strings.
* **dissectRequiredParameters**: A recursive private method utilized internally to dissect and gather required parameters from nodes connected to the function node.

**Example Use Case**

Let's consider a use case where you have to create a function to handle user authentication in a graph:

1. A Function node is initialized with the name parameter set to “UserAuthentication”.
2. Inside the function, nodes to handle the authentication process such as verifying user credentials are added.
3. "Get Function Parameter" nodes are used within the function to retrieve the parameters passed during the call, which in this case might be username and password.
4. After the authentication process, an "Add Function Result" node is used to set a return value indicating the success or failure of the authentication.
5. In another part of the graph, a "Call Function" node is used to call the “UserAuthentication” function with the necessary parameters.
6. The return values from the function call are then utilized in subsequent nodes to control the flow of the graph based on the authentication result.

By defining a user authentication function, developers can create a reusable and organized structure, enhancing the modularity and readability of the graph. This facilitates easier debugging and maintenance of the graph in the long term.

***

I hope this suits your needs. If you have any specific details to add or change, feel free to let me know!
