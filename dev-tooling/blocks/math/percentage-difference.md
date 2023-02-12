# Percentage Difference

`Percentage Difference` blocks calculate the percentage difference between two given numbers, with respect to the first of the two numbers.

`Percentage Difference` blocks have two input parameters called "A" and "B". Their output expresses what percent "A" would need to change for it to be equal to "B". This is equivalent to _100(B - A) / A_.

As with all block types in the [`Math`](./) category, `Percentage Difference` blocks are non-executive blocks, which means that they have no yellow connectors, and thus they are never called explicitly by other blocks, and they themselves cannot call other blocks. Instead, they are called implicitly whenever their output is required as input by some other block that is executing. We can observe this happening in the example below.

<figure><img src="https://i.imgur.com/0crIZ27.png" alt=""><figcaption></figcaption></figure>

In the example above, we use a `Percentage Difference` block to compare the market capitalizations of ETH and BTC in order to calculate what percentage ETH needs to gain before it flips BTC's market cap.

When the graph starts, we use a sequence of two [`Get CoinGecko Coin`](../coingecko/get-coingecko-coin.md) blocks to retrieve the market capitalizations of ETH and BTC, and we then feed these market cap values into the `Percentage Difference` block. Note that we link up ETH as "A" and BTC as "B", which means that the output will be the percentage change Ether needs to undergo to reach Bitcoin's market cap, rather than the other way around.

After calculating our percentage difference, we pass that value to a [`Round`](round.md) block in order to format it into a more displayable form, and then we pack it into a short message using a [`Replace String In String`](../string/replace-string-in-string.md) block. Finally, we record that message in the graph's logs using a [`Print`](../log/print.md) block.

In our example, we simply calculate and then print the percentage difference between ETH and BTC market caps one time, right when the graph starts running. It is easy to imagine a more robust and complete example in which this calculation is done whenever requested by users on some platform like Discord or Telegram.&#x20;

\
