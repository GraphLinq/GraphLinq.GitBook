# Get CoinGecko Coin

`Get CoinGecko Coin` blocks are used to access various pieces of current data about a coin or token from CoinGecko. With `Get CoinGecko Coin` blocks we can access price, all-time high, 24-hour market cap change, market cap, and 24-hour volume.

`Get CoinGecko Coin` blocks have one input parameter, which is a string called "Symbol". This parameter must be given the name of the coin or token we want to look up as it exists on CoinGecko. The easiest way to figure this out is to navigate to your coin or token's page on [coingecko.com](https://www.coingecko.com/en), and then look at the last part of the URL that comes after the final slash.

In the following simple example, we use a `Timer` block to call a `Get CoinGecko Coin`block every five seconds. The `Get CoinGecko Coin` block then retrieves Bitcoin's current data from CoinGecko, and passes the price to a [`Print`](../log/print.md) block to be recorded in our graph's log.

<figure><img src="https://i.imgur.com/WexrmlY.png" alt=""><figcaption></figcaption></figure>

This next example is much more advanced. It involves using a Discord bot to listen to a Discord channel for a particular command ("/btc\_csv"), and, when the command is detected, uploading a CSV file containing Bitcoin's current stats (price, all-time high, 24-hour market cap change, market cap, and 24-hour volume) to the Discord channel:

<figure><img src="https://i.imgur.com/SITlU0P.png" alt=""><figcaption></figcaption></figure>

The example above begins by using a [`Discord Connector`](../discord/discord-connector.md) block to establish a Discord connection through a Discord bot whose token we control. Then we use an [`On Discord Channel Message`](../discord/on-discord-channel-message.md) block to listen to all messages in a given Discord channel. Each time a message is detected in the channel, it is passed to a [`String Branch`](../base-condition/string-branch.md) block which we use to check if the message is equal to the command we are listening for, "/btc\_csv". When we detect this command, we execute our `Get CoinGecko Coin` block, which retrieves all of Bitcoin's current data for us from CoinGecko.

In this example, we are using all five of the `Get CoinGecko Coin` block's outputs, even though we haven't connected any of them to other blocks with dotted-line data connections. This is because we are using a special block called `Convert Last Node Parameters To CSV Row` after our `Get CoinGecko Coin` block. This block takes all the output data of the previous block (whatever is connected to it with a yellow connection), and converts it into a CSV row (comma-separated values, a standardized format for storing data), which it then outputs as the output parameter "Row".

With the help of a `Create CSV` block, an `Add CSV Row` block, and a `Convert CSV To File` block, we add this row of data (containing the five pieces of data output by the `Get CoinGecko Coin` block) to a new CSV object and then convert the CSV object into a CSV file. Finally, using a [`Send Discord Channel File`](../discord/send-discord-channel-file.md) block, we upload our new CSV file (which we name btc.csv) to the same channel that we detected the "/btc\_csv" message in. \
