# Set Function Result

Define and set results for a function in your graph logic The "Set Function Result" node is an instrumental tool within the GraphLinq IDE, allowing developers to assign values to the result parameters of a function, defining what it will return upon execution. This node plays a pivotal role in defining a function's output, enhancing the interoperability and dynamics of various functionalities within a graph.

**Block Description**

Situated under the Function category in the GraphLiq IDE, the "Set Function Result" node is designed to facilitate the definition of result parameters for a function, dictating what it will return after execution. It establishes the outcomes of a function, helping in molding different paths and logic depending upon the function's results, thereby promoting dynamic and reactive graph designs.

**Input Parameters**

The "Set Function Result" node requires a series of inputs representing the results or output values that a function will return post-execution. Developers have the liberty to define various types of data as output, tailoring the function to meet different requirements and scenarios.

**Properties**

The properties of this node will be intrinsically linked to the nature and type of results that the function is envisioned to return. While setting up this node, developers will assign values to different result parameters, establishing a blueprint of the function's output dynamics.

**Output**

While the "Set Function Result" node primarily functions to establish the result parameters of a function, it does not have an output parameter in the traditional sense. Its role is centered around defining what a function node will output after being executed in a graph, laying the groundwork for subsequent nodes to function based on the results produced.

**Example Use Case**

To understand the application and potential of the "Set Function Result" node, let's delve into a practical scenario involving a user validation function:

1. A "Set Function Result" node is introduced into a graph, linked to a function node representing a user validation process.
2. Within the function setup, inputs such as "isValidUser" and "validationMessage" are established, representing the potential results of the function.
3. The "Set Function Result" node defines the values that these result parameters will hold, creating pathways for different outcomes, such as successful validation or an error message.
4. As the function executes, depending upon the input parameters and internal logic, it navigates to the "Set Function Result" node to determine the values to return.
5. The function returns the defined results, which can then be utilized by other nodes in the graph to steer the logic in different directions, be it welcoming a valid user or prompting an invalid user to try again.

By implementing the "Set Function Result" node, developers gain control over a function's output dynamics, promoting a responsive and adaptive graph environment that reacts based on the outcomes defined and returned by various functions.
