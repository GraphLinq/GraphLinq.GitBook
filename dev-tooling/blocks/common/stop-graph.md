# Stop Graph

The Stop Graph block is used to halt the execution of a graph at a specific point in the workflow. When the Stop Graph block is executed, it immediately stops the entire graph, preventing any further actions or operations from being executed.

In the example below, the Stop Graph block is used to create a conditional termination of the graph:

<figure><img src="https://images.unsplash.com/photo-1572670014853-1d3a3f22b40f?crop=entropy&#x26;cs=srgb&#x26;fm=jpg&#x26;ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHw2fHxTdG9wfGVufDB8fHx8MTY5MDU1OTkzOXww&#x26;ixlib=rb-4.0.3&#x26;q=85" alt=""><figcaption></figcaption></figure>

When the graph is run, the flow of execution reaches the Stop Graph block. If the specified condition is met (in this case, "isMarketClosed" is true), the graph will terminate immediately. Otherwise, if the condition is false, the graph will continue executing other blocks after the Stop Graph block.

The Stop Graph block is helpful when we need to introduce conditional termination points in our graphs, allowing us to control the flow of execution based on certain conditions or events.
