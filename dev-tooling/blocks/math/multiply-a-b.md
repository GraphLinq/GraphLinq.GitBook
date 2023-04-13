# Multiply A \* B

`Multiply A * B` blocks simply multiply two given numbers together and then output the result.

`Multiply A * B` blocks have two input parameters called "A" and "B". These are, of course, the two numbers we want to multiply together. Note that these input parameters can be supplied with any type of numeric data (decimal, integer, long), and the two data types do not need to match (ie: you can multiply a decimal value by an integer value).

As with all block types in the [`Math`](./) category, `Multiply A * B` blocks are non-executive blocks, which means that they have no yellow connectors, and thus they are never called explicitly by other blocks, and they themselves cannot call other blocks. Instead, they are called implicitly whenever their output is required as input by some other block that is executing. We can observe this happening in the example below.

<figure><img src="https://i.imgur.com/uEE7sJF.png" alt=""><figcaption></figcaption></figure>

In this example, when our graph is run, it will print the current gas price of a simple ETH transaction into the logs.

The calculation that this graph performs begins with the current price of gas in Gwei, given by the `Estimate Gas Price` block. Next, we use a `Multiply A * B` block to multiply this by 21,000, because that is how many units of gas it costs to do a simple ETH transaction. This gives of the cost of one ETH transaction in Gwei, but we want the cost of one transaction in USD. Gwei is a denomination of Ether, so we next use a [`Divide A / B`](divide-a-b.md)block to divide our price in Gwei by one billion, which converts it into the same price denominated in Ether. Finally, we use a second `Multiply A * B` block to multiply this number by the current USD price of Ether as given by the [`Get CoinGecko Coin`](../../blocks-exchange/coingecko/get-coingecko-coin.md) block, which gives us the current USD gas cost of a simple ETH transaction.

In our example, we simply calculate and then print the price of an Ether transaction one time, right when the graph starts running. It is easy to imagine a more developed and useful example in which this calculation is done whenever requested by users on some platform like Discord or Telegram.

\
