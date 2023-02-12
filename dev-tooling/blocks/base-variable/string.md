# String

`String` blocks allow us to enter string-type data into our graphs. Strings are sequences of characters. They can contain letters, digits, spaces, symbols, and so on.

`String` blocks are very useful in constructing GLQ graphs, as, among other things, they allow us to:

\-Name our variables (and to later retrieve them by name)\
\-Input important data like contract and wallet addresses\
\-Create messages to be sent as emails or output by bots (Telegram, Discord, Twitter)\
\-Capture and parse messages sent by users, for example in a Telegram channel

The following graph snippet is a simple example of a `String` block being used to input a CoinGecko token name into a [`Get CoinGecko Coin`](https://docs.graphlinq.io/blockTypes/29-coinGecko/1-getCoinGeckoCoin) block in order to output that token's 24h volume into the logs:

<figure><img src="https://i.imgur.com/kRsz0yP.png" alt=""><figcaption></figcaption></figure>

The next example is much more involved, and demonstrates several uses of `String`blocks in a single graph:

<figure><img src="https://i.imgur.com/P1ziudW.png" alt=""><figcaption></figcaption></figure>

This graph listens to Telegram messages through a Telegram bot. Whenever a user sends the message "/maticprice" in a channel the bot is in, the bot will reply in that same channel with a message containing the price of Matic.

The first `String` block on the left is used to inform the graph of the Telegram bot's access token, so that the graph knows which Telegram bot to use. Whenever the `On Telegram Message` block detects that a message has been heard by the Telegram bot, it sends that message to the [`String Branch`](../base-condition/string-branch.md) block to be compared to the string "/maticprice". If the strings match (== output on the [`String Branch`](../base-condition/string-branch.md) block), then we execute a `Get Uniswap Token Price` block, using another `String` block to indicate Matic's contract address. Finally, we construct an output string by passing the string "The price of Matic is: ${0}" to a [`Replace String In String`](../string/replace-string-in-string.md) block, and telling it to replace the "{0}" with whatever price the `Get Uniswap Token Price` block retrieved. This message is then handed to a `Send Telegram Message` block, which will cause the Telegram bot to send that message in the Telegram channel.

Note: The [`Variable Portal`](variable-portal.md) blocks at the top are used simply to pass references of the Telegram channel and bot that detected the command along to the `Send Telegram Message` block, so that the response is delivered by the same bot and in the same channel that the command was detected.

In addition to what is shown above, strings can also be merged together using [`Concat String`](../string/concat-string.md) blocks, and strings can be searched to see if they contain other strings using [`String Contains`](../string/string-contains.md) blocks.\
