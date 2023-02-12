# Event Trigger Type

The event Type is the node type that receive data from streams of third parties like Binance, Uniswap, Ethereum, Binance smart chain.. And internal cycle start events, such as Timer node.

Current deployed events list over the Engine network:

```
"Block Type" -> "NodeBlock.Engine.Nodes.OnGraphStartNode"
"Description" -> "This event is called when the graph start, usefull for initialize variables"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.TimerNode"
"Description" -> "Start a timer that will init a new execution cycle, from in parameter specified time."
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Plugin.Ethereum.Nodes.OnNewBlockEventNode"
"Description" -> "Event that occurs everytime a new ethereum block is minted"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Plugin.Ethereum.Nodes.OnNewTransactionEventNode"
"Description" -> "Event that occurs everytime a new ethereum transaction appears in the last network block"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Plugin.Ethereum.Nodes.Wallet.OnWalletTransaction"
"Description" -> "Event that watch a specific wallet addr and return the details of any new transaction"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Plugin.Ethereum.Nodes.Uniswap.OnUniswapSwapNode"
"Description" -> "Event that trigger on each new swap request on Uniswap from a specific token smart-contract address"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Plugin.Ethereum.Nodes.Uniswap.OnUniswapSyncNode"
"Description" -> "Event that occurs on liquidity providers update on a specific contract address, returning the reserve of both token left in the pool"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Plugin.Ethereum.Nodes.BSC.OnNewBSCBlockNode"
"Description" -> ""
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Plugin.Ethereum.Nodes.BSC.PankakeSwap.OnPancakeSwapNewPairNode"
"Description" -> ""
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Plugin.Ethereum.Nodes.BSC.PankakeSwap.OnPancakeSwapSwapNode"
"Description" -> ""
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Plugin.Exchange.Nodes.Binance.OnBinancePairTickerUpdateNode"
"Description" -> "Get a event when the book ticker is updated on Binance for a symbol"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Plugin.Messaging.Nodes.Twitter.OnUserTweetNode"
"Description" -> "This event allow you to track tweets from a user"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Plugin.Messaging.Nodes.Telegram.OnMessageTelegramBotNode"
"Description" -> "This event allow you to handle a message from Telegram in your graph"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Plugin.Messaging.Nodes.Discord.OnDiscordPrivateMessageNode"
"Description" -> "Trigger a event when you receive a private message on Discord"
"Block Gas Cost" -> 0
```
