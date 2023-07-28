# Long

The Long block allows us to enter large whole number values into our graphs. It is similar to the Integer block but supports much larger values, as it is stored as a 64-bit signed integer. This block is useful when dealing with data that exceeds the range of regular integers.

In the following example, we use a Long block to specify a timestamp for a scheduled event in our graph:

<figure><img src="https://placehold.co/600x400" alt=""><figcaption></figcaption></figure>

When the above graph is run, it schedules the execution of a specific event at the timestamp provided by the Long block. The Long block allows us to handle large values for timestamps, ensuring precision and accuracy in time-related operations within the graph.

As with other base variable data types, we can use blocks to save and retrieve Long values at runtime, enabling persistent data storage and retrieval.

Conceptually, `Long` blocks are no different from [`Integer`](integer.md) blocks: they both allow us to enter whole number values into our graphs.

The only difference between the integer data type and the long data type is the amount of memory allocated to store the data, which determines the maximum values we can use these data types for.

Integers are 32-bit, which means they can be used for any whole numbers from about negative 2.1 billion to positive 2.1 billion. Longs, on the other hand, are 64-bit, which means they can store any whole numbers between about negative 9.2 quintillion and positive 9.2 quintillion.
