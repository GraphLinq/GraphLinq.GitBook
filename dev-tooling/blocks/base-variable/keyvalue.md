# KeyValue

The KeyValue block allows us to store and access key-value pairs of data in our graphs. It is similar to dictionaries or maps in other programming languages, where each value is associated with a unique key. This block is particularly useful when we need to manage and manipulate data in a structured way.

In the example below, we use a KeyValue block to store information about different cryptocurrencies and their corresponding prices:

When the above graph is executed, it stores the key-value pairs for Bitcoin (BTC), Ethereum (ETH), and Cardano (ADA) with their respective prices in a structured manner. Later in the graph, we use a Get Variable block to access and retrieve the price of Ethereum (ETH) from the KeyValue block and pass it as input to another block for further processing.

The KeyValue block provides a convenient way to manage data and organize information in our graphs, making it easier to access and use specific values when needed. Additionally, we can modify, update, or remove key-value pairs at runtime, allowing for dynamic data management within the graph.
