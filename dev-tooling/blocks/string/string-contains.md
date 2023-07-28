# String Contains

The [String Contains](string-contains.md) block is a versatile component in the GraphLinq IDE used to check if a specific substring exists within a given string. It is invaluable for performing conditional checks and making decisions based on the presence or absence of certain patterns in the input strings.

**Usage:**

The [String Contains](string-contains.md) block takes two string inputs: the main string and the substring. It then evaluates whether the substring is a part of the main string. If the substring is found within the main string, the block outputs a boolean value "true"; otherwise, it outputs "false."

**Example:**

Suppose we have a string "GraphLinq is awesome," and we want to check if it contains the substring "awesome." We can use the "String Contains" block with the main string as "GraphLinq is awesome" and the substring as "awesome." The block will return "true" because the substring "awesome" is present in the main string.

**Advantages:**

The "String Contains" block empowers developers to create conditional logic within their graphs. By checking for specific substrings, graphs can dynamically adapt their behavior based on user input or real-time data, making applications more interactive and responsive.

**Summary:**

The "String Contains" block in the GraphLinq IDE provides a straightforward way to determine if a particular substring exists within a given string. It enables the implementation of conditional checks and dynamic decision-making in graphs, enhancing the graph's ability to respond intelligently to different scenarios.









`String Contains` blocks make it possible to search through a string to see if it contains some other string. This allows us to sift through text from whatever sources and check for certain words or phrases.

In the following example, we check every message that a Telegram bot hears to see if it contains the string "forbidden phrase". If it hears "forbidden phrase", it sends a warning message in the same Telegram channel that it heard the message in.

<figure><img src="https://i.imgur.com/OFJALXJ.png" alt=""><figcaption></figcaption></figure>

In this next example, we listen to tweets from some particular Twitter account, and if they contain "Bitcoin" or "btc", a message is printed to the logs with a [`Print`](../log/print.md) block.

<figure><img src="https://i.imgur.com/dts2eUx.png" alt=""><figcaption></figcaption></figure>

In the above example, we use a `String Contains` block to check every tweet made by FamousTwitterHandle. We first check to see if the tweet contains "Bitcoin". If it doesn't then we use a second `String Contains` block to see if it contains "btc". Note that `String Contains` blocks are not case sensitive, so this graph would also detect "bitcoin" and "BTC".

If the `String Contains` blocks detect either "Bitcoin" or "btc" (or "bitcoin" or "BTC"), then we print a message about it into the logs. Note that we could do something more interesting after detecting a phrase in a tweet, like send a message from a Discord bot, send ourselves an email or phone notification, or even deploy a buy or sell order on Binance.\
