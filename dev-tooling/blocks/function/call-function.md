# Call Function

Invoke a defined function with specified parameters The "Call Function" node serves as a vital component in the GraphLinq IDE, enabling developers to call previously defined functions within a graph, and pass the necessary parameters for execution. It acts as a bridge, initiating the execution of a function and facilitating the structured flow of data through various functional blocks.

**Block Description**

Found under the Function category in the GraphLiq IDE, the "Call Function" node plays the indispensable role of invoking a function in your graph. This node promotes reusability and organization, allowing for a cleaner, more modular approach to developing complex systems by encapsulating functionalities into callable functions.

**Input Parameters**

The node requires the definition of a series of input parameters which are essentially the set of arguments that are to be passed to the function it is calling. These parameters should correspond to the expected parameters of the function being called, ensuring a seamless transfer and manipulation of data.

**Properties**

Within the properties of the "Call Function" node, you will specify the function to be called and map the input parameters to the function’s expected parameters, facilitating a correct data handover for the function’s execution.

**Output**

After a successful function call, this node outputs the results returned by the called function. These results can then be utilized by other nodes in the graph, providing a dynamic and responsive approach to managing various functionalities in a cohesive manner.

**Example Use Case**

To better understand the functionalities of the "Call Function" node, let’s consider a hypothetical scenario where a function for user validation is being utilized:

1. A function for validating user data is previously defined in the graph, having inputs like "username" and "password" and returning results such as "validationStatus" and "validationMessage".
2. The "Call Function" node is integrated into the graph workflow, where it is tasked to call the user validation function.
3. Input parameters for "username" and "password" are passed to the "Call Function" node, initiating the validation process.
4. The node calls the user validation function with the provided inputs, which then executes and returns the validation results.
5. The returned results, which include "validationStatus" and "validationMessage", are then collected by the "Call Function" node and can be forwarded to other nodes for further processes, such as informing the user of their validation status.

By leveraging the "Call Function" node, developers can create a structured, organized, and modular graph, encapsulating specific functionalities into callable functions, thus enhancing the efficiency and readability of the graph logic.
