# Add Emoji On Message

`Add Emoji On Message` blocks allow us to react to a particular Discord message with an emoji of our choosing through either a Discord bot that we control or a Discord user account that we control (depending on what data we give to our [`Discord Connector`](discord-connector.md)block).

`Add Emoji On Message` blocks have five input parameters. Like all Discord-related blocks, `Add Emoji On Message` blocks require a Discord connection established by a `Discord Connector` block. They also require the guild (server) ID of the Discord server the message is on, the Discord channel ID of the channel the message is on, and the message ID of the message itself. Finally, they have a string parameter called "Emoji" that should be supplied with the actual emoji we want to react with, like the brain in the example below.

The example below is an extension of the example on the [`Add Role User`](add-role-user.md) page. It is recommended to familiarize yourself with the example on that page before considering this one.

<figure><img src="https://i.imgur.com/7Ty0s9K.png" alt=""><figcaption></figcaption></figure>

In the example above, once our bot has sent the message that instructs users to react to the message with a brain emoji, we then use an `Add Emoji On Message` block to have our bot react to its own message with a brain emoji. This makes it more convenient for users to react with a brain emoji, since they can now just click on the bot's own brain reaction to add their own copy of the same reaction and solve the captcha, rather than needing to search for the correct emoji in the emoji menu.

In general, note that Discord guild (server) IDs and Discord channel IDs can be found by right-clicking on a server or channel in the Discord app and clicking on "Copy ID". Similarly, it is possible to acquire the message ID of a message that has already been sent in a Discord channel by right-clicking on the message in Discord and clicking "Copy ID".
