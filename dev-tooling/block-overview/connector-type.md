# Connector Type

Connector node types are node connected flux stream over different type of networks, decentralized and centralized such as websocket, tcp connections or UDP fluxs.

Current deployed connector type list over the Engine network:

```
"Block Type" -> "NodeBlock.Plugin.Ethereum.Nodes.EthConnection"
"Description" -> "Connection to the Ethereum network, can be used as Managed connection (without in parameters) or with your own node"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Plugin.Ethereum.Nodes.Etherscan.EtherscanConnectorNode"
"Description" -> "Connection to the Etherscan API"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Plugin.Ethereum.Nodes.BSC.BSCConnectorNode"
"Description" -> ""
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Plugin.Exchange.Nodes.Binance.BinanceConnectorNode"
"Description" -> "Binance connector, for retrieve your ApiKey and ApiSecret go to your Binance account and create them"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Plugin.Messaging.Nodes.Twitter.TwitterConnector"
"Description" -> "Twitter connector, it allow you to track tweets users or tweet some text to create credentials go here https://developer.twitter.com/en/apps/create"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Plugin.Messaging.Nodes.Telegram.TelegramBotInstanceNode"
"Description" -> "Telegram connector, to retrieve your AccessToken talk to BotFather to create a new bot"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Plugin.Messaging.Nodes.Discord.DiscordConnector"
"Description" -> "Discord Connector, allow you to receive and send messages on discord guilds"
"Block Gas Cost" -> 0
```
