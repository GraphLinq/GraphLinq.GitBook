# Divide A / B

`Divide A / B` blocks divide one given number by another and then output the result.

`Divide A / B` blocks have two input parameters called "A" and "B". These are the two numbers that we want to get the quotient of. Note that these input parameters can be supplied with any type of numeric data (decimal, integer, long), and the two data types do not need to match (ie: you can divide a decimal value by an integer value).

As with all block types in the [`Math`](./) category, `Divide A / B` blocks are non-executive blocks, which means that they have no yellow connectors, and thus they are never called explicitly by other blocks, and they themselves cannot call other blocks. Instead, they are called implicitly whenever their output is required as input by some other block that is executing. We can observe this happening in the example below.

<figure><img src="https://i.imgur.com/sZ3v4vk.png" alt=""><figcaption></figcaption></figure>

In this example, we are calculating the 24-hour volume of Bitcoin as a percentage of its market capitalization. After using a [`Get CoinGecko Coin`](../coingecko/get-coingecko-coin.md) block to access current statistics about Bitcoin, we use our `Divide A / B` block to divide Bitcoin's 24-hour trade volume with its market cap to get the ratio between them, which is the first step in calculating a percentage. We then use a [`Multiply A * B`](multiply-a-b.md) block to multiply this ratio by 100, which is the second and final step in calculating a percentage.

Once we have calculated the percentage, we use a [`Replace String In String`](../string/replace-string-in-string.md) block to construct a short message including our result, and then print it into the graph's logs using a [`Print`](../log/print.md) block.

Note that the yellow executive output on the [`Get CoinGecko Coin`](../coingecko/get-coingecko-coin.md) block is plugged directly into the [`Print`](https://docs.graphlinq.io/blockTypes/5-log/1-print) block, which means that this is the next block to be called after the `Get CoinGecko Coin` block. However, for the `Print` block to execute, its "Message" parameter must be supplied with a value. This causes the [`Replace String In String`](../string/replace-string-in-string.md)block to resolve, which in turn causes the `Multiply A * B` block to resolve, which finally causes our `Divide A / B` block to resolve. This is an example of implicit calling, where a non-executive block is called only when its output is required by some other block's input.

In our example, we simply calculate and then print Bitcoin trade volume as a percentage of market cap one time, right when the graph starts running. It is easy to imagine a more advanced and utile example in which this calculation is done whenever requested by users on some platform like Discord or Telegram.

\
