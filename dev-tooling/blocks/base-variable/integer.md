# Integer

The `Integer` block allows us to enter whole number values into our graphs by linking an `Integer` block's output to an integer type input of another block.

In the following graph snippet, we use an `Integer` block to enter the integer 10 as an input into the `Get Uniswap Token Price` block:

<figure><img src="https://i.imgur.com/Lro9Co3.png" alt=""><figcaption></figcaption></figure>

When the above graph is run, the price value output by the `Get Uniswap Token Price`block will be the price of 10 of the tokens specified by the contract address in the [`String`](../string/)block.

This is an example of using an `Integer` block to specify an integer literal, which is an integer whose value is known by the developer when they develop the graph, and can therefore be entered directly as we have done with the number 10. As with all the other base variable data types, we can also save integer values determined at runtime as persistent variables using [`Set variable`](set-variable.md) blocks, and we can retreive those values later using [`Get variable`](get-variable.md) blocks.
