# On Discord Private Message

`On Discord Private Message` blocks are event blocks that fire whenever a specified Discord account or Discord bot receives a private Discord message.

`On Discord Private Message` blocks only have one input: a Discord connection that must be provided by a [`Discord Connector`](discord-connector.md) block. The Discord account or bot token that is provided to the `Discord Connector` we use will determine which account or bot our `On Discord Private Message` block will be listening to private messages for.

`On Discord Private Message` blocks output several pieces of data:

\-A string called "From" which will be equal to the Discord username of the message sender.\
\-A string called "Message" which will be equal to the contents of the private message.\
\-An integer called "MessageId" which is an identifier for the message we have received. This can be used as input for any block type that requires a reference to a message, like [`On Reaction Added Message`](on-reaction-added-message.md) blocks.\
\-A variable called "Author", which is a reference to the Discord account that sent the private message. This is used specifically to plug into the "Author" input of [`Reply Private Discord Message`](reply-private-discord-message.md) blocks, in order to indicate which Discord user it should be replying to.

In the following example, whenever our Discord bot receives a private message, we detect it with our `On Discord Private Message` block, and then send it to a [`String Branch`](../base-condition/string-branch.md)block to check if the message equals "good bot". If it does, then we use a `Reply Private Discord Message` block to send a thank-you message back to the user who sent the "good bot" message.

<figure><img src="https://i.imgur.com/paNc2Lp.png" alt=""><figcaption></figcaption></figure>

Note that the "Author" output of the `On Discord Private Message` block is plugged into the [`Reply Private Discord Message`](reply-private-discord-message.md) block to indicate that the reply should be made to the same user that sent the original private message.

In this example, our thank-you message is customized to include the username of the Discord user who sent the original private message. We achieve this by constructing our message with a [`Replace String In String`](../string/replace-string-in-string.md) block, and feeding the "From" output of our `On Discord Private Message` block into the "ReplaceText" input of the `Replace String In String` block.\
