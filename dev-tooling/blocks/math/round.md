# Round

The Round block in the GraphLinq IDE is a fundamental mathematical component used to round a given numeric value "A" to the nearest whole number or a specified number of decimal places. It provides a convenient method to adjust the precision of numeric data, ensuring that the output conforms to the desired level of accuracy.

Block Details: The Round block takes two input parameters: "A" and "Decimal Places." "A" represents the numeric value that needs to be rounded, and "Decimal Places" is an optional parameter that allows developers to specify the number of decimal places to which the value should be rounded. If "Decimal Places" is not provided, the block rounds "A" to the nearest whole number.

Execution: Like other blocks in the Math category, the Round block is non-executive, meaning it does not have yellow connectors. Instead, it is implicitly called whenever its output is needed as input by other executing blocks. When the Round block's output is required in a graph, it performs the rounding operation on the input value "A" and delivers the rounded result as its output.

Use Case: The Round block finds extensive applications in various scenarios where precision in numeric data is critical. It is commonly used in financial calculations, statistical analyses, and data visualizations. For instance, in financial applications, rounding is essential for representing monetary values in a standardized format. In statistics, rounding data helps maintain a consistent level of significance across datasets. In data visualizations, rounded values improve readability and eliminate unnecessary detail.

Example: Let's consider an example to illustrate the usage of the Round block. Suppose we have a graph that calculates the average temperature for a given day, based on hourly temperature measurements. The graph takes the sum of hourly temperatures (A) and the number of measurements (B) as inputs and needs to compute the average temperature.

To achieve this, we first use the Divide A / B block to calculate the average temperature, which might result in a decimal value with multiple decimal places. However, for display purposes, we want to round the average temperature to two decimal places.

To achieve the desired rounding, we can use the Round block with "Decimal Places" set to 2. By providing the calculated average temperature to the Round block and specifying "2" for the "Decimal Places" parameter, the block rounds the value to two decimal places and outputs the rounded average temperature.

The Round block's ability to round numeric values to a specified precision enables developers to control the level of detail in their graphs' outputs. It enhances the presentation of numeric data and ensures that calculations conform to the desired level of accuracy.







`Round` blocks are used to round a given decimal number to a given degree of precision.

`Round` blocks have two input parameters: "Number", which is the number we would like to have rounded, and which should be a decimal type value, and "Decimal", which (somewhat confusingly) is an integer that represents how many digits of precision we would like to the right of the decimal point.

As with all block types in the [`Math`](./) category, `Round` blocks are non-executive blocks, which means that they have no yellow connectors, and thus they are never called explicitly by other blocks, and they themselves cannot call other blocks. Instead, they are called implicitly whenever their output is required as input by some other block that is executing. We can observe this happening in the example below.

In this example, we are using a Discord bot that we control in conjunction with a [`String Branch`](../base-condition/string-branch.md) block to listen to our Discord channel for the message "/matic\_price". When we detect that someone has sent that message, we use a [`Get CoinGecko Coin`](../../blocks-exchange/coingecko/get-coingecko-coin.md) block to retrieve the current price of the Matic token. We then use our `Round` block to round the price to 3 digits of precision (for example, $1.124) before adding it into a short message using a [`Replace String In String`](../string/replace-string-in-string.md) block and then submitting that message to our Discord channel with our bot using a [`Send Discord Channel Message`](../../blocks-messaging/discord/send-discord-channel-message.md) block.\
