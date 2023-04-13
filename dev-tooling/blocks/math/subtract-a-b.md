# Subtract A - B

`Subtract A - B` blocks subtract one given number from another, and then output the result.

`Subtract A - B` blocks have two input parameters called "A" and "B". These are, of course, the two numbers we want to calculate the difference of. Note that these input parameters can be supplied with any type of numeric data (decimal, integer, long), and the two data types do not need to match (ie: you can subtract a decimal value from an integer value).

As with all block types in the [`Math`](./) category, `Subtract A - B` blocks are non-executive blocks, which means that they have no yellow connectors, and thus they are never called explicitly by other blocks, and they themselves cannot call other blocks. Instead, they are called implicitly whenever their output is required as input by some other block that is executing. We can observe this happening in the example below.

<figure><img src="https://i.imgur.com/ysZT8Hf.png" alt=""><figcaption></figcaption></figure>

This example is somewhat involved. The point of this graph is to print the 5-minute candle delta (change in price over 5 minutes) of the GLQ token, every 5 minutes. Since we are calculating the difference of two prices, we benefit from the use of a `Subtract A - B`block.

This graph has two parts. The part in the upper-left quadrant is an initialization structure. When the graph starts, we use a [`Get CoinGecko Coin`](../../blocks-exchange/coingecko/get-coingecko-coin.md) block to get the price of GLQ, and then we save it in a variable called "lastPrice" with a [`Set variable`](../base-variable/set-variable.md) block.

The rest of the graph is driven by a `Timer` block, which fires every 5 minutes (300 seconds). Whenever it fires, it calls a `Get CoinGecko Coin` block, which retrieves the current price of GLQ. This price is then passed to our `Subtract A - B` block, which substracts from it the price from 5 minutes before (stored in the variable "lastPrice"). The output of our `Subtract A - B` block is thus the 5-minute price delta of GLQ. We pack this into a short message using a [`Replace String In String`](../string/replace-string-in-string.md) block and then print it into the graph's log using a [`Print`](../log/print.md) block. Finally, we use a `Set variable` block to assign the current price of GLQ to the variable "lastPrice", so that when the `Timer` block next fires in 5 minutes, that variable will contain the 5-minute-old price of GLQ.

Note that the yellow executive output on the `Get CoinGecko Coin` block is plugged directly into the `Print` block, which means that this is the next block to be called after the `Get CoinGecko Coin` block. However, for the `Print` block to execute, its "Message" parameter must be supplied with a value. This causes the `Replace String In String`block to resolve, which in turn causes the `Subtract A - B` block to resolve. This is an example of implicit calling, where a non-executive block is called only when its output is required by some other block's input.

\
