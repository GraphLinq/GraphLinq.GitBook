# Is Variable Exist

`Is Variable Exist` blocks are used to check if a variable by some name has already been declared (created) at an earlier point in the graph's execution by a [`Set variable`](set-variable.md)block.

`Is Variable exist` blocks have one input parameter: a string representing the variable name we are inquiring about. They have two executive outputs labelled "True" and "False". If a variable by the given name exists, then the "True" connection will be executed. Otherwise, the "False" connection will be executed.

<figure><img src="https://i.imgur.com/yGeqS4U.png" alt=""><figcaption></figcaption></figure>

In the graph snippet above, we use an `Is Variable Exist` block to check if a variable already exists by the name "exampleVariable". If such a variable does exist, we access its value using a [`Get variable`](get-variable.md) block, and then output it with a [`Print`](../log/print.md) block. Otherwise, we print a message about how the requested data has not yet been established.

The example below is more advanced, but it demonstrates a realistic use of the `Is Variable Exist` block:

<figure><img src="https://i.imgur.com/Q7xjJBl.png" alt=""><figcaption></figcaption></figure>

This graph outputs the change in Bitcoin's price over the last minute, once every minute, so long as the graph is left running. It does this with the use of a `Timer` on a 60-second cycle. Once a minute, the timer triggers a [`Get CoinGecko Coin`](../coingecko/get-coingecko-coin.md) block, which accesses the current price of Bitcoin and then subtracts from that the value of a variable called "priceOneMinuteAgo", and then prints the result. Afterwards, it uses a [`Set variable`](set-variable.md)block to overwrite the value of "priceOneMinuteAgo" with the current price of Bitcoin. That way, when the timer next triggers 60 seconds from now, that variable will then contain a 1-minute-old price of Bitcoin.

The purpose of the `Is Variable Exist` block here comes from the observation that, the very first time the `Timer` block triggers and this sequence runs, the variable "priceOneMinuteAgo" won't exist yet, as it hasn't been declared yet with a [`Set variable`](set-variable.md)block. This means that it won't be possible to use this variable in a subtraction operation: the calculated result would end up just being empty. Therefore, we use an `Is Variable Exist` block to check if "priceOneMinAgo" exists yet. If so, we execute the full sequence like normal. If not, then we skip the subtraction and printing this cycle, and simply go ahead and use the [`Set variable`](set-variable.md) block to declare and assign to the variable "priceOneMinuteAgo".

The effect of this technique in this example is that the very first time this algorithm cycles, the `Is Variable Exist` block will output "False", and then every subsequent cycle it will output "True".\
