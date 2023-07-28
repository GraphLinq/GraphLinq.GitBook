# Decimal Branch

The Decimal Branch blocks in the GraphLinq IDE are fundamental tools for creating conditional branching based on decimal values. These blocks evaluate the input decimal data and determine the appropriate path of execution within the graph based on the specified conditions.

Decimal Branch blocks have two main output paths: the True path and the False path. The decision on which path to follow depends on the evaluation of the condition set by the developer. If the condition evaluates to true, the graph will execute the nodes connected to the True output. If the condition evaluates to false, the nodes connected to the False output will be executed.

To set the condition for the Decimal Branch, developers can use a variety of comparison operations, such as greater than (">"), less than ("<"), equal to ("=="), not equal to ("!="), greater than or equal to (">="), and less than or equal to ("<="). These operations allow for precise and flexible conditional checks based on the decimal inputs.

### Example

In this example, we have a Decimal Branch block that checks if the input decimal value "price" is greater than 50. If the condition is true, the graph will execute the nodes connected to the True output, which might perform actions like placing a buy order. If the condition is false, the graph will follow the nodes connected to the False output, which might perform other actions like placing a sell order or doing nothing.

Decimal Branch blocks are versatile components that enable developers to create powerful decision-making logic within their graphs. By using conditional checks based on decimal values, developers can create dynamic and responsive applications that can adapt to changing market conditions or other data inputs. The Decimal Branch category is an essential tool for building complex and sophisticated graphs in GraphLinq.



***

### More Information

`Decimal Branch` blocks are used to control executive flow according to a comparison of two decimal numbers.

`Decimal Branch` blocks are very similar to [`Integer Branch`](integer-branch.md) blocks; the only difference is that the two numbers being compared are decimals, not integers.`Decimal Branch` blocks have two input parameters, which are the decimal numbers we want to compare. They have five yellow output connectors, corresponding to the following five scenarios: the first number is > greater than the second, the first number is >= greater than or equal to the second, the two numbers are == equal, the first number is <= less than or equal to the second, and the first number is < less than the second.&#x20;

<figure><img src="https://i.imgur.com/PzaUH1U.png" alt=""><figcaption></figcaption></figure>

In the example above, we use a `Timer` block to check the price of XLM on CoinGecko once an hour. Using a `Decimal Branch` block, we check to see if the price of XLM is below $0.20. If it is, we print a message to the logs with a [`Print`](../log/print.md) block.

The `Print` block at the end is a placeholder example. In a more fleshed out scenario, a graph that is checking for a price crash like this might send a phone notification, or even execute a trade on Binance. \
