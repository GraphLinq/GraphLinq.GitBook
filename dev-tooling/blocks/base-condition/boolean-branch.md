# Boolean Branch

`Boolean Branch` blocks are used to control the executive flow (which yellow connection will fire next) based upon the value of a boolean variable.

`Boolean Branch` blocks have one input parameter, which is the boolean that will determine the output. While it is possible to provide this boolean input as an actual [`Boolean`](../base-variable/boolean.md) block that has had "true" or "false" typed into it, there wouldn't be much point to this, as the `Boolean Branch` block would always fire in the exact same way, since the input has been typed in as a fixed value (equivalent to using a boolean literal in programming).

It makes more sense to provide the input to a `Boolean Branch` block using a [`Get variable`](../base-variable/get-variable.md) block that retrieves the value of a boolean variable that was previously declared with a [`Set variable`](../base-variable/set-variable.md) block. In this way, we can use `Boolean Branch` blocks to determine paths of execution based upon the values of boolean variables.

The following example is in two parts, but they are part of the same graph. The goal here is to allow Telegram users to use commands to turn a notification bot on and off. The bot outputs the price of Bitcoin in a Telegram channel every 60 seconds when it is on.

In the first part, we are listening to Telegram messages that are picked up by our Telegram bot. For each message heard, we are using [`String Branch`](string-branch.md) blocks to check whether the message equals "/turnNotifsOn" or "/turnNotifsOff". If either of these strings are detected then we use `Set variable` blocks to set the value of a variable called "priceNotificationsOn" to "true" or "false", respectively.

<figure><img src="https://i.imgur.com/ZorTP01.png" alt=""><figcaption></figcaption></figure>

In the second part of the example, we have a `Timer` block that fires every minute. Whenever it fires, we execute a `Boolean Branch` block. We use a [`Get variable`](../base-variable/get-variable.md) block to access the value of the variable called "priceNotificationsOn" (the same variable that Telegram users are able to set thanks to the first part of our example). If the value of "priceNotificationsOn" is "true", then the `Boolean Branch` will trigger the [`Get CoinGecko Coin`](../../blocks-exchange/coingecko/get-coingecko-coin.md) block, and we will end up outputting the price of Bitcoin into the Telegram channel. Otherwise, nothing will happen, and we will reevaluate in 60 seconds when the `Timer` block fires again.\


<figure><img src="https://i.imgur.com/2OUFxLQ.png" alt=""><figcaption></figcaption></figure>
