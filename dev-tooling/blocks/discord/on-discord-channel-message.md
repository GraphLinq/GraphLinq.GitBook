# On Discord Channel Message

`On Discord Channel Message` blocks are event blocks that fire every time a message is sent by any user in a particular Discord channel. This allows us to listen to every message said in a Discord channel, which, among other things, enables us to detect and react to specific bot command strings, and generally to parse user messages and search through them for specific keywords/substrings.

Like all Discord-related blocks, `On Discord Channel Message` blocks require a Discord connection as an input parameter. This connection should be provided by a [`Discord Connector`](discord-connector.md) block. `On Discord Channel Message` blocks also require a Discord channel ID as input; this can be found by right-clicking on the channel in the Discord app and then clicking "Copy ID".

`On Discord Channel Message` blocks output three pieces of data. The most important one is called "Message"; this is a string that is equal to whatever message was said in the Discord channel that triggered the `On Discord Channel Message` block. By analysing this piece of data, we can create logic that depends upon the content of the messages we are listening to. For example, we can detect specific commands using [`String Branch`](../base-condition/string-branch.md)blocks, or search through the message for certain substrings using [`String Contains`](../string/string-contains.md)blocks in order to react to various keywords.

`On Discord Channel Message` blocks also output the Discord guild (server) ID and channel ID where the message was detected, which can be convenient to use as inputs to others blocks that should be interacting with the same Discord channel, like the [`Send Discord Channel Message`](send-discord-channel-message.md) block in the example below.

In the example below, we are using an `On Discord Channel Message` block to listen to every message said in a Discord channel in order to compare each message to several special keywords that we are using as bot commands, like "/menu" and "/price". Whenever one of the messages heard by the `On Discord Channel Message` block is equal to one of the keywords we are checking for, then we can execute the appropriate part of the graph for the command we have detected.

<figure><img src="https://i.imgur.com/WDJDKJF.png" alt=""><figcaption></figcaption></figure>

In the example above, we start by setting up a Discord API connection through a bot we control by passing our bot's token to a `Discord Connector` block. Then, we use an `On Discord Channel Message` block to listen to every message sent in our Discord channel. Each time it detects a message, it sends it to a [`String Branch`](../base-condition/string-branch.md) block where it is compared to the string "/menu". In the case that our user's message does equal "/menu", then we execute a [`Send Discord Channel Message`](send-discord-channel-message.md) block that we can imagine sends a message in the Discord channel that displays a menu of all the bot commands we offer.

If the message isn't equal to "/menu", we pass it along to another `String Branch` block to see if it is instead equal to "/price", in which case we would presumably output the price of a crypto asset.

This chaining of `String Branch` blocks is a common way to check if a message is equal to one of several strings that we care about. In programming, this technique would be analogous to an `if` statement followed by several `else if` statements. In the example above, it is implied that we continue this cascading technique beyond the bottom right corner of the image, in order to support multiple bot commands.
