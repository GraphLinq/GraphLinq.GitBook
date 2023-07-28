---
description: >-
  Replace occurrences of a specified substring in a given input string with a
  new string
---

# Replace String in String

The [Replace String In String](replace-string-in-string.md) block in the GraphLinq IDE is a powerful tool that allows developers to modify strings by replacing specific substrings with new content. This block is invaluable for performing string manipulation and transforming text-based data within graphs. It provides essential functionalities for efficiently modifying strings and adapting them to various scenarios.

## Block Description

&#x20;The [Replace String In String](replace-string-in-string.md) block is part of the [String](./) category in the GraphLinq IDE. Its primary function is to replace occurrences of a specified substring in a given input string with a new string. This enables developers to make precise modifications to textual data within their graphs.

**Input Parameters:** The [Replace String In String](replace-string-in-string.md) block requires three input parameters:

1. Input String (String Type): This parameter represents the original input string that contains the substrings to be replaced.
2. Search String (String Type): The Search String input represents the substring to be searched for in the input string. Whenever this substring is found, it will be replaced with the new string.
3. Replace With String (String Type): The Replace With String input is the new content that will replace all occurrences of the Search String in the Input String.

### Output

The output of the Replace String In String block is a modified version of the original Input String with all instances of the Search String replaced with the Replace With String. The output string is the result of the precise replacements performed by this block.

### Example Use Case

Let's explore a practical example to illustrate how the Replace String In String block can be used in a graph:

1. The graph receives data from an external source that contains user feedback.
2. The Input String variable stores this user feedback.
3. The Search String is set to identify specific keywords or phrases, such as "bad," "disappointed," or "unhappy."
4. The Replace With String is set to a more positive and uplifting phrase, such as "great," "satisfied," or "happy."
5. The Replace String In String block then processes the Input String and replaces all instances of the negative keywords with the positive phrases.
6. The final output from the Replace String In String block will be the user feedback with all negative words replaced with positive ones, creating a more positive and encouraging message.

In this example, the [Replace String In String](replace-string-in-string.md) block enables the graph to process user feedback and transform it into more positive and constructive responses. This empowers developers to improve user experiences by providing more encouraging and supportive interactions with their applications.

The Replace String In String block is an essential tool in the GraphLinq IDE for efficiently modifying textual data within graphs. Its ability to replace specific substrings in an input string with new content allows developers to perform precise string manipulation and tailor responses to various scenarios. By utilizing the Replace String In String block, developers can enhance user interactions, provide more personalized feedback, and create more engaging and user-friendly applications.



***



### More Information

The [Replace String in String](replace-string-in-string.md) block is a crucial element in the GraphLinq IDE that allows developers to modify strings by replacing specific substrings with new content. It is useful for performing string manipulation and transforming text-based data in graphs.

#### Usage

The [Replace String in String](replace-string-in-string.md) block requires three string inputs: the original string, the substring to be replaced, and the new content that will replace the substring. The block then searches for occurrences of the substring within the original string and replaces all occurrences with the new content.

#### Example

Let's illustrate the usage of the [Replace String in String](replace-string-in-string.md) block with an example. Suppose we have a string "I enjoy GraphLinq," and we want to replace "enjoy" with "love." By using the [String](../base-variable/string.md) block with the original string as "I enjoy GraphLinq," the substring to be replaced as "enjoy," and the new content as "love," the block will output the modified string "I love GraphLinq."

#### Advantages

The [Replace String in String](replace-string-in-string.md) block provides a powerful mechanism for manipulating strings within graphs. It enables developers to replace specific text patterns, correct data, or tailor messages dynamically based on changing requirements.

#### Summary

The [Replace String in String](replace-string-in-string.md) block in the GraphLinq IDE offers a valuable feature for altering strings by replacing designated substrings with new content. It facilitates string transformation, data correction, and dynamic message generation within graphs, enhancing the overall flexibility and functionality of graph designs.



***



### Full Example

`Replace String in String` blocks allow us to replace all instances of a specific substring found within some string with a third string. They have three inputs: "Original" is the main string, "ToReplace" is the substring that we are searching for within "Original", and "ReplaceText" is the string that we want to replace every instance of "ToReplace" with.&#x20;

`Replace String in String` blocks are commonly used to add some data that is acquired or calculated during runtime to some kind of message tempate, as we do here:

<figure><img src="https://i.imgur.com/Cvk90bE.png" alt=""><figcaption></figcaption></figure>

This produces:&#x20;

<figure><img src="https://i.imgur.com/OaRaiwY.png" alt=""><figcaption></figcaption></figure>

In the example above, we use the string "{0}" as a sort of placeholder in our original string. We then search for "{0}" using our `Replace String in String` block, and replace that string with whatever price is returned by the[ `Get CoinGecko Coin`](../../blocks-exchange/coingecko/get-coingecko-coin.md) block.

We could have used any string for our placeholder here; we used "{0}" because it is conventional. Note that if more than one instance of "{0}" (or whatever your "ToReplace" string is) exists in the original string, they will all be replaced with the "ReplaceText" string. Also note that we are allowed to put integer or decimal type data in the "ReplaceText" input parameter, as we do above with Bitcoin's price. The numeric data will be converted to string data behind the scenes before it is substituted into the original string. Below is an example of chaining several `Replace String in String` blocks to create an output message containing many pieces of data:

<figure><img src="https://i.imgur.com/uf0xw8a.png" alt=""><figcaption></figcaption></figure>

This produces:&#x20;

<figure><img src="https://i.imgur.com/SristQQ.png" alt=""><figcaption></figcaption></figure>

This kind of technique would likely be used for any kind of bot that is supposed to output a bunch of stats about some coin or token when prompted.\
