# Get variable

The Get Variable block allows us to retrieve the value of a previously stored variable within the graph's data context.

&#x20;The Get Variable block allows us to retrieve the value of a previously stored variable within the graph's data context that had previously been declared and assigned to by [`Set variable`](set-variable.md) block.

In the example below, we use the Get Variable block to retrieve the previously stored value of "priceThreshold" and use it as an input for the Check Price block:

<figure><img src="https://images.unsplash.com/photo-1504868584819-f8e8b4b6d7e3?crop=entropy&#x26;cs=srgb&#x26;fm=jpg&#x26;ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHwyfHxncmFwaHxlbnwwfHx8fDE2OTA1NTYzMzl8MA&#x26;ixlib=rb-4.0.3&#x26;q=85" alt=""><figcaption></figcaption></figure>

When the above graph is executed, the Get Variable block fetches the value of "priceThreshold," which was previously stored in the data context, and passes it as input to the Check Price block for price comparison. This enables us to use data that has been calculated or determined earlier in the graph, allowing for efficient and structured data flow.

`Get variable` blocks have one input: a string for the name of the variable we are accessing. They also have one output, which is the value of the variable we have accessed.

The purpose of `Get Variable` and [`Set variable`](set-variable.md) blocks is to be able to store data in variables that can be accessed and modified later on in a graph's execution

If no variable exists with the name that we pass to a `Get variable` block, then it will simply output no data, and any block receiving as input the `Get Variable` block's output will instead receive empty (or null) data.&#x20;

Refer to the [`Set variable`](set-variable.md) block page for examples of `Get variable` and [`Set variable`](set-variable.md) blocks in action.
