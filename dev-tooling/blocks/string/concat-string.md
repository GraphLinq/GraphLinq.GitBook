# Concat String

The [Concatenate String](concat-string.md) block, often referred to as "[Concat String](concat-string.md)," is a fundamental component in the GraphLinq IDE for working with strings. As the name suggests, this block is used to concatenate or combine multiple strings into a single string.

**Usage:**

The [Concatenate String](concat-string.md) block takes two strings as inputs and merges them together to form a new string. The output of this block is the result of combining the input strings. It provides a simple yet powerful way to create dynamic messages, generate meaningful information, or construct complex text outputs in graphs.

**Example:**

Let's consider a practical example where we have two strings, "Hello" and "World." By using the "Concatenate String" block, we can merge these two strings into a single greeting message, such as "Hello World." The block takes "Hello" as one input and "World" as another, and the output will be the concatenated string "Hello World."

**Advantages:**

The [Concatenate String](concat-string.md) block allows developers to dynamically build strings based on various inputs, making it ideal for generating customized messages and responses within graphs. It enhances the flexibility and versatility of graph designs by enabling the creation of dynamic content based on real-time data or user interactions.

**Summary:**

The [Concatenate String](concat-string.md) block in the GraphLinq IDE is a powerful tool for merging multiple strings into a single coherent string. It is widely used for creating dynamic messages, generating informative outputs, and building flexible applications that respond to different scenarios with customized text. With the ability to combine strings easily, developers can craft engaging and interactive experiences within their graphs.







`Concat String` blocks are used to combine two strings into one string. They take three strings as input: the two strings you want to merge together, and a delimiter string. When a `Concat String` block executes, it will stick the second string onto the end of the first string, with the delimiter string inserted between them. If you don't provide a delimiter, then it will default to a space character.

<figure><img src="https://i.imgur.com/DQnDLC5.png" alt=""><figcaption></figcaption></figure>

In the above example, we are looking up the price of Bitcoin on CoinGecko. Then, we are using a `Concat String` block to combine the string "Bitcoin price:" with whatever price is output by the [`Get CoinGecko Coin`](../../blocks-exchange/coingecko/get-coingecko-coin.md) block. The resulting concatenated string is then passed to the [`Print`](../log/print.md) block as a single string, where it is printed to the logs looking something like:

<figure><img src="https://i.imgur.com/5WOMkUO.png" alt=""><figcaption></figcaption></figure>

Note that in the above example, we didn't pass anything as the third "Delimiter" input of the `Concat String` block. Therefore, the default space character was used, which is why there is a space between the_:_ and the _3_.

If instead, we attach a [`String`](../base-variable/string.md) block as the delimiter of the `Concat String`, but then leave the string empty, then no delimiter will be used, and our two strings will be merged directly together with nothing between them, like in the following example:

<figure><img src="https://i.imgur.com/rg4euOT.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://i.imgur.com/ngMNuYc.png" alt=""><figcaption></figcaption></figure>

It is also possible to insert a line break between our strings by pressing enter after clicking in the [`String`](https://docs.graphlinq.io/blockTypes/1-baseVariable/6-string) block like so:

<figure><img src="https://i.imgur.com/8AefqhX.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://i.imgur.com/CqLDZgZ.png" alt=""><figcaption></figcaption></figure>
