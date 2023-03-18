# Function Type

The function Type is the node type that perform a specific task: it execute a fixed action (set of multiple instructions) inside your graph.

Current deployed function list over the Engine network:

```
"Block Type" -> "NodeBlock.Engine.Nodes.FetchHTTPNode"
"Description" -> "Make an HTTP GET request to any requested server"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.GetTimestampNode"
"Description" -> "Return the current timestamp of the engine localtime"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.JsonSelectorNode"
"Description" -> "Select a specific value in a json object and return it as string parameter"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.PrintNode"
"Description" -> "Display a message in the console logs"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.StopGraphNode"
"Description" -> "Stop the execution of the current graph"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.Vars.GetVariable"
"Description" -> "Return the value of the variable pre computed from a Set variable block"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.Vars.SetVariable"
"Description" -> "Set a variable value (can be any type) in the graph memory context"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.Text.StringConcat"
"Description" -> "Split two string by a specific delimiter and return it as out parameter."
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.Text.StringReplaceNode"
"Description" -> "Replace some part of the original string by a new strings"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.Storage.GetKeyItemNode"
"Description" -> "Return a specific key from the Redis storage allocated for the graph execution"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.Storage.KeyItemExistNode"
"Description" -> "Check if a specific key from the Redis storage exist"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.Storage.SaveKeyItemNode"
"Description" -> "Save a specific key in the Redis storage allocated for the graph execution"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.Math.AddNode"
"Description" -> "Calculate the value of A + B (both sent in params) and return it as out parameter"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.Math.BounceRateIntervalNode"
"Description" -> "Calculate the bounce rate in the given interval, you can use the Percentage value only when the OnIntervalTick trigger"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.Math.DivideNode"
"Description" -> "Calculate the division of value of A / B (both sent in params) and return it as out parameter, zero division are forbidden."
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.Math.ModuloNode"
"Description" -> "Calculate the Modulo of value of A % B (both sent in params) and return it as out parameter."
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.Math.MultiplyNode"
"Description" -> "Calculate the multiplication of value of A * B (both sent in params) and return it as out parameter."
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.Math.PercentageDiffNode"
"Description" -> "Calculate the percentage difference of value of A from B (both sent in params) and return difference as out parameter."
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.Math.SubtractNode"
"Description" -> "Calculate the substraction of value of A - B (both sent in params) and return it as out parameter."
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.Encoding.ConvertLastBlockOutputToJsonNode"
"Description" -> "Serialize the last node executed in the graph to JSON data"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.Encoding.ConvertToJsonNode"
"Description" -> "Convert the received any type parameter into a JSON object readable"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.Encoding.StringToBase64Node"
"Description" -> "Transform a clear string into a base64 string as output"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.Data.CombineDataNode"
"Description" -> "Combine two data in single one"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.Data.ConvertNodeToDataNode"
"Description" -> "Convert output parameters to data parameters"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.Data.SendDataToWebhookNode"
"Description" -> "Send data parameters as JSON to the url specified"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.CSV.AddCSVColumnNode"
"Description" -> "Add a new column to a csv"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.CSV.AddCSVRowNode"
"Description" -> "Add a row to a csv"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.CSV.AddCSVRowValue"
"Description" -> "Add a value to a csv row"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.CSV.ClearCSVNode"
"Description" -> "Clear CSV Rows"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.CSV.ConvertCSVToDataNode"
"Description" -> "Convert CSV to data parameters"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.CSV.ConvertCSVToFileNode"
"Description" -> "Convert CSV to file"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.CSV.ConvertLastNodeParametersToCSVRowNode"
"Description" -> "Convert last node out parameters to CSV row"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.CSV.CreateCSVNode"
"Description" -> "Create a new CSV instance"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.CSV.CreateCSVRowNode"
"Description" -> "Create new csv row"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.CSV.GetCSVRowsCountNode"
"Description" -> "Get CSV Rows Count"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.Branch.ExecutionTimeIntervalNode"
"Description" -> "Allow execution in a interval rate"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Plugin.Ethereum.Nodes.Uniswap.GetUniswapPairPriceNode"
"Description" -> "Return the pair price of an Uniswap pool as out parameters"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Plugin.Ethereum.Nodes.Eth.Transaction.GetBlockTransactionParametersNode"
"Description" -> "Parse the last Ethereum block object received into string out parameters readable"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Plugin.Ethereum.Nodes.Eth.Transaction.GetTransactionParametersNode"
"Description" -> "Parse the last Ethereum transaction object received into string out parameters readable"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Plugin.Ethereum.Nodes.Etherscan.GetGasPriceNode"
"Description" -> "Return the current GAS Price on the Ethereum blockchain as out parameter"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Plugin.Exchange.Nodes.CoinGecko.GetCoinGeckoSimplePriceNode"
"Description" -> "Get CoinGecko Coin Data"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Plugin.Exchange.Nodes.Binance.BinanceAvgPriceNode"
"Description" -> "Get the current average price on binance for a symbol"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Plugin.Exchange.Nodes.Binance.BinanceGetVolumeNode"
"Description" -> "Get the 24h volume on binance for a symbol"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Plugin.Exchange.Nodes.Binance.GetBinanceFutureUSDTRSINode"
"Description" -> "Get Binance Future USDT RSI for a symbol"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Plugin.Exchange.Nodes.Binance.GetBinanceMarketRSINode"
"Description" -> "Get Binance Market RSI for a symbol"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Plugin.Messaging.Nodes.Twitter.TweetMessageNode"
"Description" -> "Tweet a message on Twitter"
"Block Gas Cost" -> 0
```

<pre><code>"Block Type" -> "NodeBlock.Plugin.Messaging.Nodes.Telegram.SendTelegramMessageNode"
<strong>"Description" -> "Send a message on Telegram"
</strong>"Block Gas Cost" -> 0
</code></pre>

```
"Block Type" -> "NodeBlock.Plugin.Messaging.Nodes.Discord.SendDiscordFileOnGuildNode"
"Description" -> "Send a file on a guild channel"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Plugin.Messaging.Nodes.Discord.SendDiscordMessageOnGuildNode"
"Description" -> "Send a message on a guild channel"
"Block Gas Cost" -> 0
```

[\
](https://docs.graphlinq.io/blocks)
