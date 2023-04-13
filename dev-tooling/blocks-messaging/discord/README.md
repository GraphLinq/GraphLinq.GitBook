# Discord

This block category includes all block types that pertain to Discord, a messaging service and community platform.

\`[Discord Connector](discord-connector.md)\` blocks are used to establish a connection to the Discord API, which is a necessary step before using any other block type in this category.

We can detect Discord commands as well as general messages in a Discord channel using `On Discord Command` and [`On Discord Channel Message`](on-discord-channel-message.md) blocks. Using `On Discord Private Message` blocks, we can also detect private messages received by the user whose token we initialized our Discord connection with.

We can reply to private messages using `Reply Private Discord Message` blocks, and send messages and files to Discord channels using [`Send Discord Channel Message`](send-discord-channel-message.md)and [`Send Discord Channel File`](send-discord-channel-file.md) blocks.

It is also possible to add and remove Discord server roles from users using [`Add Role User`](add-role-user.md) and [`Remove Role User`](remove-role-user.md) blocks.

Finally, we can add emoji reactions to messages using [`Add Emoji On Message`](add-emoji-on-message.md) blocks, and detect when and by whom specific emoji reactions are added or removed from specific comments using [`On Reaction Added Message`](on-reaction-added-message.md) and [`On Reaction Removed Message`](on-reaction-removed-message.md) blocks.
