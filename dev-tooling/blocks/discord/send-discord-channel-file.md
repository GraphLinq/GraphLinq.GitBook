# Send Discord Channel File

As the name suggests, `Send Discord Channel File` blocks are used to upload files to a Discord channel, either through a Discord bot or a Discord user account (depending on what inputs we pass to our [`Discord Connector`](https://docs.graphlinq.io/blockTypes/39-discord/3-discordConnector) block).

`Send Discord Channel File` blocks operate in a very similar fashion to [`Send Discord Channel Message`](https://docs.graphlinq.io/blockTypes/39-discord/12-sendDiscordChannelMessage) blocks. Like [`Send Discord Channel Message`](https://docs.graphlinq.io/blockTypes/39-discord/12-sendDiscordChannelMessage) blocks, they require a Discord connection provided by a [`Discord Connector`](https://docs.graphlinq.io/blockTypes/39-discord/3-discordConnector) block, which will specify the bot or user account through which the file sending will be done. They also require a Discord guild (server) ID and a Discord channel ID.

The guild ID and channel ID for any Discord channel can be found in the Discord App by right-clicking on either the guild (server) or channel, and then clicking "Copy ID".

In the example below, users in a Discord channel are able to send the message "/get\_ETH\_CSV", and in response our graph will upload a CSV file called "eth\_csv" to the discord channel:&#x20;

<figure><img src="https://i.imgur.com/y5nhLRA.png" alt=""><figcaption></figcaption></figure>

There are a couple of implications with the image above.

For one thing, it is implied that, elsewhere in the graph, a variable called "discord" has been assigned a Discord connection through the use of a [`Discord Connector`](https://docs.graphlinq.io/blockTypes/39-discord/3-discordConnector) block and a [`Set variable`](https://docs.graphlinq.io/blockTypes/1-baseVariable/9-setVariable) block. In the image above, we are accessing that variable twice with [`Get variable`](https://docs.graphlinq.io/blockTypes/1-baseVariable/7-getVariable) blocks, for the two Discord-related blocks that require Discord connections. The values given to the implied [`Discord Connector`](https://docs.graphlinq.io/blockTypes/39-discord/3-discordConnector) block would determine which Discord user account or bot is used to send the file.

The other implication with the example above is that a CSV-type variable has been declared elsewhere in the graph by the name of "ethCSV". It is easy to imagine having something like a timer set up that adds data about Ethereum to a CSV at regular intervals. Whenever the part of our graph pictured above detects the message "/get\_ETH\_CSV", it uses a [`Get variable`](../base-variable/get-variable.md) block to access the CSV that we have presumably been adding data to. We then convert that CSV object into an actual file with the name "eth.csv", and then upload it into the Discord channel with our `Send Discord Channel File` block.

For the "GuildID" and "Channel" input parameters of our `Send Discord Channel File`block, we simply link in the equivalently-named output parameters of the [`On Discord Channel Message`](on-discord-channel-message.md) block, which means that the file will be uploaded to the same channel and guild as the "/get\_ETH\_CSV" message was detected in.

\
