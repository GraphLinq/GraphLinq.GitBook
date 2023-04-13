# Round

`Round` blocks are used to round a given decimal number to a given degree of precision.

`Round` blocks have two input parameters: "Number", which is the number we would like to have rounded, and which should be a decimal type value, and "Decimal", which (somewhat confusingly) is an integer that represents how many digits of precision we would like to the right of the decimal point.

As with all block types in the [`Math`](./) category, `Round` blocks are non-executive blocks, which means that they have no yellow connectors, and thus they are never called explicitly by other blocks, and they themselves cannot call other blocks. Instead, they are called implicitly whenever their output is required as input by some other block that is executing. We can observe this happening in the example below.

In this example, we are using a Discord bot that we control in conjunction with a [`String Branch`](../base-condition/string-branch.md) block to listen to our Discord channel for the message "/matic\_price". When we detect that someone has sent that message, we use a [`Get CoinGecko Coin`](../../blocks-exchange/coingecko/get-coingecko-coin.md) block to retrieve the current price of the Matic token. We then use our `Round` block to round the price to 3 digits of precision (for example, $1.124) before adding it into a short message using a [`Replace String In String`](../string/replace-string-in-string.md) block and then submitting that message to our Discord channel with our bot using a [`Send Discord Channel Message`](../../blocks-messaging/discord/send-discord-channel-message.md) block.\
