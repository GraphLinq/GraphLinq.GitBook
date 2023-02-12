# Decimal Range Branch

`Decimal Range Branch` blocks are used to control executive flow (which yellow connection will fire next) based upon whether a given decimal value is above (or equal to) the upper bound of a range, or below (or equal to) the lower bound of a range.

`Decimal Range Branch` blocks have three inputs, all of type decimal: "Value" is the number that we are checking against the range, "RangeMax" defines the upper bound of the range, and "RangeMin" defines the lower bound of the range.

If "Value" is greater than or equal to "RangeMax", then the first executive connection will fire. If "Value" is less than or equal to "RangeMin", then the second executive connection will fire.

Note that if "Value" is inside the range defined by "RangeMin" and "RangeMax", then nothing will happen. `Decimal Range Branch` blocks are only for detecting when "Value" is outside the range.

In the following example, we use a `Decimal Range Branch` block to send a message to a Telegram channel if the price of ADA goes above $2.00 or below $1.00:

<figure><img src="https://i.imgur.com/M8IGfDy.png" alt=""><figcaption></figcaption></figure>

The example above is driven by the `Timer` block, which fires every 60 seconds. When the `Timer` block fires, it triggers the [`Get CoinGecko Coin`](../coingecko/get-coingecko-coin.md) block, which retrieves the present price of ADA. This price is then passed to our `Decimal Range Branch` block, which compares it to the range $1.00 - $2.00.

If the price is above the upper bound, then our Telegram bot will send the message "ADA has broken above $2.00!" to our Telegram channel using a `Send Telegram Message`block and a `Telegram Bot` block. If the price is below the lower bound, then our Telegram bot will send the message "ADA has fallen below $1.00!" to our Telegram channel.

If the price of ADA is inside the range, then the flow of execution will end at the `Decimal Range Branch` block, and our graph will wait for the `Timer` block to fire again a minute later.

\
