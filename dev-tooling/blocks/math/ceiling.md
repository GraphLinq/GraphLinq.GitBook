# Ceiling

`Ceiling` blocks are used to round numbers up to the nearest integer. They are very similar to [`Floor`](floor.md) blocks; the only difference between the two is that `Ceiling` blocks round up (so 5.01 -> 6), whereas `Floor` blocks round down (so 5.99 -> 5).

`Ceiling` blocks only have one input parameter called "Number", which is the number that we would like to round up. The logical data type for this parameter is decimal.

As with all block types in the [`Math`](./) category, `Ceiling` blocks are non-executive blocks, which means that they have no yellow connectors, and thus they are never called explicitly by other blocks, and they themselves cannot call other blocks. Instead, they are called implicitly whenever their output is required as input by some other block that is executing. We can observe this happening in the example below.

<figure><img src="https://i.imgur.com/FcrN5HV.png" alt=""><figcaption></figcaption></figure>

In the example above, we are simply calculating and printing the lowest amount of entire Bitcoins worth at least $1 million at the current market price as per CoinGecko.

We use a [`Get CoinGecko Coin`](../coingecko/get-coingecko-coin.md) block to fetch the price of Bitcoin once when the graph begins its execution. We then divide 1 million by the current price of Bitcoin using a [`Divide A / B`](divide-a-b.md) block. This gives us the true amount of Bitcoin which is equivalent to $1 million dollars. For example, if BTC currently costs $35,000, this calculation would result in 28.57 BTC. However, we want the lowest amount of the _whole_ BTC worth at least $1 million, which is where our `Ceiling` block comes in. Once we ceiling this value, we get 29, which is then packed into a short message using a [`Replace String In String`](../string/replace-string-in-string.md) block, and recorded in the graph's logs with a [`Print`](../log/print.md) block.&#x20;

Note that the yellow executive output on the [`Get CoinGecko Coin`](../coingecko/get-coingecko-coin.md) block is plugged directly into the `Print` block, which means that this is the next block to be called after the `Get CoinGecko Coin` block. However, for the `Print` block to execute, its "Message" parameter must be supplied with a value. This causes the `Replace String In String`block to resolve, which in turn causes the `Ceiling` block to resolve (which then causes the `Divide A / B` block to resolve). This is an example of implicit calling, where a non-executive block is called only when its output is required by some other block's input.

\
