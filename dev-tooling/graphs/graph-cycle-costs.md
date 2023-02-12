# Graph Cycle Costs

As you saw in the previous page, a graph has a direct path between its start and the end of the execution, event triggers such as Connector blocks can create new events that trigger a new graph cycle.

Easier: Every block that starts a new trigger, from event or time-based, will init a new execution cycle that will occur more blocks of nodes and can create new cycles of nodes depending on your execution path of that cycle.

Since every block type has a fixed GAS as GLQ price you can directly now calculate the estimated cost for running a specific task on a Graph.

But be careful: since you can have an infinite number of cycles regardings the starting point that you have set (events, triggers, conditions..) the estimated fixed price is not the same as the dynamic that will depend on the number of times you're event get triggered.

A more concrete example with a random block price: If you watch every new block coming from the Ethereum Blockchain then add a Twitter message every time it occurs with the base Twitter block costing 1 GLQ at each execution, your graph price will get raised by 1 GLQ every 15 seconds (average graphlinq block time).

But now if you decide to do the same but with every new transaction, even if the Twitter block base cost is 1 GLQ, you will have to pay a higher relevant price based on the number of time the Twitter block got executed.

Be assured that we will be watching the entire graphs costs and will do the best to keep it as lower as possible, we had to put the system in place into the Protocol to prevent an overload of our network and abuse from malicious attacks.
