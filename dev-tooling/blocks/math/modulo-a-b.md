# Modulo A % B

`Modulo A % B` blocks output the result of a modulo operation\* of two given numbers.&#x20;

As you might imagine, `Modulo A % B` blocks have two input parameters called "A" and "B". In the division that determines the output of the modulo operation, "A" is the numerator and "B" is the denominator. Both of these input parameters should be of the integer data type.

One of the most common uses of the modulo operator is as a divisibility check for the purpose of tracking every _nth_ instance of something. For example, say we want to detect programatically if we are in a fiscal quarter end month. Those happen every 3 months; in other words, they happen in every month whose number is divisible by 3. Whenever a number is divisible by another, the result of the first number % the second number will always be 0. So, we can simply check if  \[current month] % 3 is equal to 0. If so, then we are in a fiscal quarter end month (3, 6, 9, or 12).

We use a similar technique in the graph below to detect every 100th Bitcoin block added to the chain:

<figure><img src="https://i.imgur.com/kEAG6jp.png" alt=""><figcaption></figcaption></figure>

In the example above, we use a Discord bot to send a message in a Discord channel that contains some data about the most recent Bitcoin block (the block height, the number of transactions, and the amount transacted). However, we don't want this to happen for every single Bitcoin block, as there are about 6 blocks added every hour, and we don't want to flood our Discord channel with 150 messages each day about new blocks. Instead, we would like to send these Discord notifications only for every 100th block added, so that our channel will be updated about Bitcoin block production only once or twice a day, which is much more reasonable.

The `On Bitcoin Block` event block will fire every time a new Bitcoin block is added to the chain. The "Height" output parameter represents the total amount of blocks on the Bitcoin chain (ie: the block number for the most recent block). If we take the modulo of that number and 100, the result will be 0 only when the block height is some multiple of 100, like 500, 6000, or 765400&#x20;

So, we use our `Modulo A % B` block to calculate the modulo between the current block height and the number 100, and then we use an [`Integer Branch`](../base-condition/integer-branch.md) to check if the result equals 0; only if it does do we proceed to build and send our Discord message. So, the `Integer Branch` the block will only call the [`Send Discord Channel Message`](../../blocks-messaging/discord/send-discord-channel-message.md) block once for every 100 times that the `On Bitcoin Block` event fires, thanks to our modulo check.

Whenever the block height does happen to be a multiple of 100, then we simply use a chain of `Replace String In String` blocks to build a message string containing the data we're interested in, and then send it to our Discord channel via some bot we control using a `Send Discord Channel Message` block.&#x20;

\*Modulo (%) operations are arithmetic operations between two operands that return the remainder after a division of the first operand by the second. For example, 7 % 3 = 1, because 3 fits into 7 2 full times, which leaves a remainder of 1. This operation is often used to determine if given numbers are even or odd, multiples/factors of other numbers, or prime.\
