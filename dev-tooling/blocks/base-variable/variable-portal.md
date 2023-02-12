# Variable Portal

``[`Variable Portal`](variable-portal.md) blocks are simply used to pipe values from one location in your graph to another.

`Variable Portal` blocks are not essential, and are never actually necessary, since it would always be possible to link your data directly from a block's output to another block's input, without first passing the data through a `Variable Portal` block. The point of `Variable Portal` blocks, then, is simply to keep your graph visually organized, and to prevent your dotted-line connections from crossing through areas of your graph that are already complicated, making things more confusing to look at. The following graph uses a Telegram bot to listen for the command "/maticprice", and to respond with a message containing Matic's price in whatever channel it heard the command:

<figure><img src="https://i.imgur.com/P1ziudW.png" alt=""><figcaption></figcaption></figure>

The `Variable Portal` blocks in this example are receiving references to the Telegram channel and Telegram bot that heard the command and then passing those references along to the `Send Telegram Message` block at the end of the graph, so that the reply is made by the same bot and in the same channel as the command occurred.

We could simply skip the `Variable Portal` blocks and instead pass that data directly from the `Telegram Bot` and `On Telegram Message` blocks to the `Send Telegram Message` block. The consequence of this would be that those two dotted white lines would pass through the middle of all our other blocks, making our graph more visually confusing.
