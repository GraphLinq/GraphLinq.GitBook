# Set variable

`Set variable` blocks are used to both declare variables and assign values to variables.

`Set variable` blocks have two inputs: a string for the variable's name, and the data that we want to assign to the variable.

The purpose of `Set variable` blocks is to store data in variables to be used later in our graph's execution with the help of [`Get variable`](https://docs.graphlinq.io/blockTypes/1-baseVariable/7-getVariable) blocks.

If the variable name that we pass to a `Set variable` block is the name of a variable that already exists, then it will simply overwrite the value of that existing variable with whatever value we passed into the `Set variable` block. If, on the other hand, no variable yet exists with the name that we pass to our `Set variable` block, then it will both declare a new variable by that name, and also initialize its value with whatever value we give to the `Set variable` block.

In the following example, we are retrieving the price of Bitcoin with a [`Get CoinGecko Coin`](https://docs.graphlinq.io/blockTypes/29-coinGecko/1-getCoinGeckoCoin) block, and then storing that value in a variable named "currentBitcoinPrice" using a `Set variable` block:

<figure><img src="https://i.imgur.com/s8pFecM.png" alt=""><figcaption></figcaption></figure>

The implication here is that we would later be accessing the value of "currentBitcoinPrice" using a [`Get variable`](https://docs.graphlinq.io/blockTypes/1-baseVariable/7-getVariable) block. While the above example does illustrate the mechanics of the `Set variable` block, it is worth noting that, in cases like this, it is often sufficient to simply plug the [`Get CoinGecko Coin`](https://docs.graphlinq.io/blockTypes/29-coinGecko/1-getCoinGeckoCoin) block directly into whatever block(s) needs its output, with no need for the middle step of first storing the data in a variable using a `Set variable` block, and then retrieving that data later when it's needed with a [`Get variable`](https://docs.graphlinq.io/blockTypes/1-baseVariable/7-getVariable) block.

Whether it makes more sense to plug data we have accessed or created directly into blocks that use that data, or to first store that data in variables using `Set variable` blocks to later access and use that data using [`Get variable`](https://docs.graphlinq.io/blockTypes/1-baseVariable/7-getVariable) blocks, is something that must be determined on a case-by-case basis.One of the most common use cases for storing our data in variables is when we want to establish something like a Binance connection or an SMTP connection one time, at the beginning of the graph's execution, to be used and reused later on in the graph's execution:

<figure><img src="https://i.imgur.com/c1Ipyyu.png" alt=""><figcaption></figcaption></figure>

In the example above, we use a `Set variable` block to declare a variable called "binanceConnector", and then assign to that variable the value of a `Binance Connector`block that has been set up with our API key and secret. Whenever we need a Binance connector later in our graph (for example to place orders on Binance), we can use this same connector by accessing our "binanceConnector" variable with a [`Get variable`](https://docs.graphlinq.io/blockTypes/1-baseVariable/7-getVariable) block.

The next example is more complicated, but it's noteworthy in that it actually requires use of the `Set variable` and [`Get variable`](https://docs.graphlinq.io/blockTypes/1-baseVariable/7-getVariable) blocks to achieve its purpose:

<figure><img src="https://i.imgur.com/PbJQmhO.png" alt=""><figcaption></figcaption></figure>

The above graph is meant to print the 1 minute percentage change in bitcoin price, every minute, for as long as we leave the graph running (we just print here to keep the example simple, but it could easily be linked up to a Telegram or Discord bot, etc).

The flow of this graph is driven by the `Timer` block, which fires every 60 seconds, triggering the [`Get CoinGecko Coin`](../../blocks-exchange/coingecko/get-coingecko-coin.md) block. The [`Get CoinGecko Coin`](../../blocks-exchange/coingecko/get-coingecko-coin.md) block passes the current price of Bitcoin to a [`Percentage Difference`](../math/percentage-difference.md) block, which computes the percentage difference between the current price of Bitcoin and the value of a variable called "priceOneMinAgo". The resulting value is added into a message, which is then logged by a [`Print`](../log/print.md) block. Finally, now that we are done calculating and printing our message for this cycle, we use a `Set variable` block to overwrite the value of "priceOneMineAgo" with the current value of Bitcoin that we retrieved with the [`Get CoinGecko Coin`](../../blocks-exchange/coingecko/get-coingecko-coin.md) block. That way, when the `Timer` block next fires in 60 seconds, the value of "priceOneMinuteAgo" will indeed be Bitcoin's price from one minute before, since one minute prior it was assigned the then-current price of Bitcoin. This allows us to repeatedly compare the current price of Bitcoin to a snapshot of Bitcoin's price from one minute prior, which would not be possible to achieve without using `Set variable` and [`Get variable`](get-variable.md) blocks. \
\
