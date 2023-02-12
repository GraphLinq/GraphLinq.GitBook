# Concat String

`Concat String` blocks are used to combine two strings into one string. They take three strings as input: the two strings you want to merge together, and a delimiter string. When a `Concat String` block executes, it will stick the second string onto the end of the first string, with the delimiter string inserted between them. If you don't provide a delimiter, then it will default to a space character.

<figure><img src="https://i.imgur.com/DQnDLC5.png" alt=""><figcaption></figcaption></figure>

In the above example, we are looking up the price of Bitcoin on CoinGecko. Then, we are using a `Concat String` block to combine the string "Bitcoin price:" with whatever price is output by the [`Get CoinGecko Coin`](../coingecko/get-coingecko-coin.md) block. The resulting concatenated string is then passed to the [`Print`](../log/print.md) block as a single string, where it is printed to the logs looking something like:

<figure><img src="https://i.imgur.com/5WOMkUO.png" alt=""><figcaption></figcaption></figure>

Note that in the above example, we didn't pass anything as the third "Delimiter" input of the `Concat String` block. Therefore, the default space character was used, which is why there is a space between the_:_ and the _3_.

If instead, we attach a [`String`](../base-variable/string.md) block as the delimiter of the `Concat String`, but then leave the string empty, then no delimiter will be used, and our two strings will be merged directly together with nothing between them, like in the following example:

<figure><img src="https://i.imgur.com/rg4euOT.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://i.imgur.com/ngMNuYc.png" alt=""><figcaption></figcaption></figure>

It is also possible to insert a line break between our strings by pressing enter after clicking in the [`String`](https://docs.graphlinq.io/blockTypes/1-baseVariable/6-string) block like so:

<figure><img src="https://i.imgur.com/8AefqhX.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://i.imgur.com/CqLDZgZ.png" alt=""><figcaption></figcaption></figure>
