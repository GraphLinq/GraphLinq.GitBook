# Decimal

The `Decimal` block allows us to enter fractional values (non-integers) into our graphs by linking a `Decimal` block's output to a decimal type input of another block. Variables of this data type are stored as 64-bit floating-point numbers.

In the following example, we use a `Decimal` block to specify a limit price of 1.20 USDT for a limit order our graph is going to place for us:

<figure><img src="https://i.imgur.com/m46Z2D5.png" alt=""><figcaption></figcaption></figure>

When the above graph is run, it will place a limit order on Binance that will cause 200 ADA to be purchased if the price of ADA gets as low as $1.20. This is an example of using a `Decimal` block to specify a decimal literal, which is a decimal whose value is known by the developer when they develop the graph, and can therefore be entered directly as we have done with the number 1.20.&#x20;

As with all the other base variable data types, we can also save decimal values determined at runtime as persistent variables using [`Set variable`](set-variable.md) blocks, and we can retreive those values later using [`Get variable`](get-variable.md) blocks.\
