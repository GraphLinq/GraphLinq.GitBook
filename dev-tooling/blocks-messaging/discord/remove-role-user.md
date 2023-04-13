# Remove Role User

`Remove Role User` blocks are used to remove Discord roles from Discord users. Discord roles are sets of permissions that define what users can and can't do in a Discord server. These roles are created and named by the owner or administrator(s) of the Discord server in question.

`Remove Role User` blocks appear and behave similarly to [`Add Role User`](add-role-user.md) blocks, with the obvious difference being that they remove roles rather than add them.

Like `Add Role User` blocks, `Remove Role User` blocks require a Discord connection from a [`Discord Connector`](discord-connector.md) block, a Discord guild (server) ID, a Discord user ID, and a string parameter called "RoleName" that should match the name of a role defined in the server settings on the Discord app.

The following example is fairly involved, as it is an expansion of the example given on the `Add Role User` page. It is recommended to familiarize yourself with the example on that page before considering this one.

In this example, we have added on the ability for a user to remove their member role by removing their brain emoji reaction. This is achieved by using an [`On Reaction Removed Message`](on-reaction-removed-message.md) block to detect the particular emoji reaction in question being removed, and a `Remove Role User` block to remove the Discord role from the user who removed the emoji reaction.

<figure><img src="https://i.imgur.com/lGfVTOf.png" alt=""><figcaption></figcaption></figure>

In general, note that Discord guild (server) IDs and Discord channel IDs can be found by right-clicking on a server or channel in the Discord app and clicking on "Copy ID". Similarly, it is possible to acquire the message ID of a message that has already been sent in a Discord channel by right-clicking on the message in Discord and clicking "Copy ID".

\
