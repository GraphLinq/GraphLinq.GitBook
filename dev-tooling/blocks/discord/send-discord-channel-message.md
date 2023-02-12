# Send Discord Channel Message

`Send Discord Channel Message` blocks are used to send messages in Discord channels either through a Discord bot or a Discord user account (depending on what inputs we pass to our [`Discord Connector`](discord-connector.md) block).

`Send Discord Channel Message` blocks have four inputs: a Discord connection (which must be established with a `Discord Connector` block), a Discord guild (server) ID, a Discord channel ID, and the message to be sent.

The guild ID and channel ID for any Discord channel can be found in the Discord App by right-clicking on either the guild (server) or channel, and then click "Copy ID".

In the example below, we send a message every 10 minutes about the price of Polygon to a specific Discord channel using a `Send Discord Channel Message` block:

<figure><img src="https://i.imgur.com/8TxwFhI.png" alt=""><figcaption></figcaption></figure>

The example above is driven by the `Timer` block, which fires every 600 seconds, triggering the [`Get CoinGecko Coin`](../coingecko/get-coingecko-coin.md) block to retrieve the price of Polygon from CoinGecko. The price is then packed into a short message using a [`Replace String In String`](../string/replace-string-in-string.md) block and finally sent to the `Send Discord Channel Message` block. This causes our Discord bot, identified by the token we give to the `Discord Connector` block, to output the message about Polygon's price in the channel and server specified by the ID strings we have supplied to the `Send Discord Channel Message` block.

`Send Discord Channel Message` blocks also output a piece of data called "MessageId", which is an identifier for the message that was sent. We could use this as input to blocks that require a message ID, like [`On Reaction Added Message`](on-reaction-added-message.md) and `On Reaction Removed Message` blocks, which could be used to track certain kinds of emoji reactions to our message.&#x20;
