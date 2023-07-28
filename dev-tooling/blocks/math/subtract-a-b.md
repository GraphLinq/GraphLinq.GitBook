# Subtract A - B

The [Subtract A - B](subtract-a-b.md) block in the GraphLinq IDE is a powerful tool for performing subtraction operations between two numeric values, A and B. This block takes two inputs, A and B, and calculates the result of subtracting B from A. The output of this operation is the difference between the two input values.

**Use Case**: The "Subtract A - B" block is incredibly useful in scenarios where you need to calculate the difference or change between two numerical values. It is commonly employed in financial applications for calculating profits or losses, in data analysis for finding variations between data points, and in various other mathematical computations that involve subtraction.

**Example**: Let's consider an example where we have two variables, A = 10 and B = 5. By connecting these variables to the "Subtract A - B" block, the result will be 5. This represents the difference between A and B.

In this example, the [Subtract A - B](subtract-a-b.md) block efficiently calculates the subtraction operation and produces the desired output of 5.









Subtract A - B

Subtract A - B blocks are powerful tools within the GraphLinq IDE, designed to calculate the difference between two numeric values, A and B. This block takes two inputs, "A" and "B," and efficiently computes the result of subtracting B from A. The output of this operation is the numerical difference between the two input values.

Block Details: Subtract A - B blocks have two input parameters: "A" and "B." These input parameters can accept various types of numeric data, such as decimal, integer, or long. Additionally, "A" and "B" can have different data types, enabling users to subtract a decimal value from an integer value or vice versa.

Execution: As with all block types in the Math category, Subtract A - B blocks are non-executive blocks. They do not have yellow connectors, which means they are not explicitly called by other blocks and cannot call other blocks themselves. Instead, they are implicitly called whenever their output is required as input by some other executing block.

Use Case: The Subtract A - B block finds extensive applications in various scenarios where numerical differences need to be calculated. It is commonly used in financial and data analysis applications for computing differences between prices, values, or data points. For instance, in the cryptocurrency domain, this block can be used to calculate price changes over time, enabling users to monitor price fluctuations.

Example: Let's consider a more involved example to showcase the utility of the Subtract A - B block. The graph's objective is to calculate and print the 5-minute candle delta (change in price over 5 minutes) of the GLQ token at regular intervals. To achieve this, the graph utilizes a Timer block set to fire every 5 minutes (300 seconds). Upon firing, the Timer block calls a Get CoinGecko Coin block to retrieve the current price of GLQ.

The Subtract A - B block then takes this current price and subtracts the price from 5 minutes ago, stored in the variable "lastPrice." The output of the Subtract A - B block represents the 5-minute price delta of GLQ. This value is further formatted into a concise message using a Replace String In String block and printed into the graph's log using a Print block.

Finally, the current price of GLQ is assigned to the variable "lastPrice," ensuring that the Timer block can access the 5-minute-old price when it next fires.

This example demonstrates the implicit calling of the Subtract A - B block, as it is only executed when its output is required by another block's input. In this case, the Subtract A - B block is an essential component for calculating and monitoring the 5-minute price fluctuations of GLQ, providing valuable insights to users.

By leveraging the Subtract A - B block, developers can perform efficient subtraction operations within their graphs, enabling them to analyze, process, and manipulate numerical data effectively. The block's versatility makes it a valuable asset in a wide range of graph designs and mathematical computations.









`Subtract A - B` blocks subtract one given number from another, and then output the result.

`Subtract A - B` blocks have two input parameters called "A" and "B". These are, of course, the two numbers we want to calculate the difference of. Note that these input parameters can be supplied with any type of numeric data (decimal, integer, long), and the two data types do not need to match (ie: you can subtract a decimal value from an integer value).

As with all block types in the [`Math`](./) category, `Subtract A - B` blocks are non-executive blocks, which means that they have no yellow connectors, and thus they are never called explicitly by other blocks, and they themselves cannot call other blocks. Instead, they are called implicitly whenever their output is required as input by some other block that is executing. We can observe this happening in the example below.

<figure><img src="https://i.imgur.com/ysZT8Hf.png" alt=""><figcaption></figcaption></figure>

This example is somewhat involved. The point of this graph is to print the 5-minute candle delta (change in price over 5 minutes) of the GLQ token, every 5 minutes. Since we are calculating the difference of two prices, we benefit from the use of a `Subtract A - B`block.

This graph has two parts. The part in the upper-left quadrant is an initialization structure. When the graph starts, we use a [`Get CoinGecko Coin`](../../blocks-exchange/coingecko/get-coingecko-coin.md) block to get the price of GLQ, and then we save it in a variable called "lastPrice" with a [`Set variable`](../base-variable/set-variable.md) block.

The rest of the graph is driven by a `Timer` block, which fires every 5 minutes (300 seconds). Whenever it fires, it calls a `Get CoinGecko Coin` block, which retrieves the current price of GLQ. This price is then passed to our `Subtract A - B` block, which substracts from it the price from 5 minutes before (stored in the variable "lastPrice"). The output of our `Subtract A - B` block is thus the 5-minute price delta of GLQ. We pack this into a short message using a [`Replace String In String`](../string/replace-string-in-string.md) block and then print it into the graph's log using a [`Print`](../log/print.md) block. Finally, we use a `Set variable` block to assign the current price of GLQ to the variable "lastPrice", so that when the `Timer` block next fires in 5 minutes, that variable will contain the 5-minute-old price of GLQ.

Note that the yellow executive output on the `Get CoinGecko Coin` block is plugged directly into the `Print` block, which means that this is the next block to be called after the `Get CoinGecko Coin` block. However, for the `Print` block to execute, its "Message" parameter must be supplied with a value. This causes the `Replace String In String`block to resolve, which in turn causes the `Subtract A - B` block to resolve. This is an example of implicit calling, where a non-executive block is called only when its output is required by some other block's input.

\
