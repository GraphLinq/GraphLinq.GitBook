# String Branch

String Branch

The String Branch blocks in the GraphLinq IDE play a crucial role in enabling conditional branching based on string values. These blocks allow developers to evaluate string data and make decisions within the graph based on specified conditions.

Like other branching blocks, the String Branch blocks have two main output paths: the True path and the False path. The determination of which path to follow depends on the result of the condition set by the developer. If the condition evaluates to true, the graph will execute the nodes connected to the True output. If the condition evaluates to false, the nodes connected to the False output will be executed.

Developers can set the conditions for the String Branch using various string comparison operations, such as checking for equality ("=="), inequality ("!="), checking for substring existence ("contains"), checking for substring absence ("not contains"), and checking for string emptiness ("is empty" or "is not empty"). These operations offer flexible ways to perform string-based conditional checks and allow for dynamic graph behavior based on string inputs.

### Example

In this example, we have a String Branch block that checks if the input string value "status" is equal to "completed". If the condition is true, the graph will execute the nodes connected to the True output, which might perform actions like updating a database or sending a success notification. If the condition is false, the graph will follow the nodes connected to the False output, which might handle different scenarios for non-completed statuses.

The String Branch blocks provide developers with the ability to implement decision-making logic based on string values within their graphs. By utilizing string comparison operations, developers can build versatile and adaptive applications that respond to specific textual conditions. The String Branch category empowers developers to create intelligent and dynamic graphs in GraphLinq, capable of handling various string-based scenarios with ease.



***

### More Information

`String Branch` blocks are used to control executive flow (which yellow connection will fire next) by comparing two strings.

`String Branch` blocks have two input parameters, which are the two strings we want to compare. They also have two yellow outputs: == fires if the two strings are equal; otherwise, != fires.

<figure><img src="https://i.imgur.com/nVdQc2p.png" alt=""><figcaption></figcaption></figure>

In the example above, we use a Telegram bot to listen for Telegram messages, and then we use a sequence of chained `String Branch` blocks to check for specific user commands.

We first use a `String Branch` block to check if the message is equal to "/menu". If it is, then we output some kind of menu into the same Telegram channel.

If it's not, then we check if it's equal to "/links". If it is, then we reply using the bot with what is presumably a list of community links.&#x20;

If the Telegram message isn't equal to that either, then we use a final `String Branch`block to check if the message is equal to "/buy". If it is, then our Telegram bot sends a message that we can imagine contains instructions on how to buy the token.

It's easy to imagine using more `String Branch` blocks to provide more functionality with our bot, like /price and /volume commands that cause the bot to output the corresponding data into the Telegram channel. \
