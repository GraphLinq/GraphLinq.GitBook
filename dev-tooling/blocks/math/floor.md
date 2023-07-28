# Floor

The Floor block in the GraphLinq IDE is a key mathematical block used to round down a numeric value to the nearest integer that is less than or equal to the original value. This block allows developers to truncate decimal or floating-point numbers and obtain whole numbers as output.

Block Details: The Floor block takes a single input parameter called "A," which represents the numeric value that needs to be rounded down. The block performs the floor operation on the input value "A" and outputs the resulting integer. "A" can be of various numeric data types, such as decimal, integer, or long.

Execution: Like other block types in the Math category, the Floor block is non-executive. It does not have yellow connectors and is implicitly called when its output is required by other executing blocks. Whenever the Floor block's output is needed in a graph, it automatically performs the floor operation on the input value "A" and provides the rounded-down integer as output.

Use Case: The Floor block is particularly useful when dealing with financial or quantitative data that involves rounding down decimal numbers to obtain whole numbers. It is commonly employed in areas such as accounting, finance, statistics, and data analysis.

Example: Let's consider an example to demonstrate the functionality of the Floor block. Suppose we have a graph that calculates the number of days required to complete a project based on the estimated total hours and the daily work capacity.

The graph takes inputs "Total Hours" (A) and "Daily Work Capacity" (B). To calculate the number of days required, we need to divide the total hours by the daily work capacity. However, we also need to consider that partial days cannot be allocated, and we want to round down to the nearest whole number of days.

Here, we can use the Floor block to perform the floor operation on the division result. The block takes the output of the division operation (A / B) and rounds it down to the nearest integer representing the number of whole days required to complete the project.

By using the Floor block in this example, we ensure that we obtain accurate and realistic estimates of the project's duration, accounting for the restriction on partial days and aligning with practical project planning.

The Floor block's ability to truncate decimal values is valuable in scenarios where precise whole numbers are necessary for further calculations, analysis, or decision-making. It provides developers with a simple yet powerful tool for handling rounding down operations and enhances the accuracy of their graphs and applications.



`Floor` blocks are used to round numbers down to the nearest integer. They are very similar to [`Ceiling`](ceiling.md) blocks; the only difference between the two is that `Ceiling` blocks round up (so 5.01 -> 6), whereas `Floor` blocks round down (so 5.99 -> 5).

`Floor` blocks only have one input parameter called "Number", which is the number that we would like to round down. The logical data type for this parameter is decimal.

As with all block types in the [`Math`](./) category, `Floor` blocks are non-executive blocks, which means that they have no yellow connectors, and thus they are never called explicitly by other blocks, and they themselves cannot call other blocks. Instead, they are called implicitly whenever their output is required as input by some other block that is executing. We can observe this happening in the example below.

<figure><img src="https://i.imgur.com/W2U8JXU.png" alt=""><figcaption></figcaption></figure>

In the simplistic example above, we are calculating and printing how many entire Bitcoins can be bought with $1 million at current market price as per CoinGecko.

We use a [`Get CoinGecko Coin`](../../blocks-exchange/coingecko/get-coingecko-coin.md) block to fetch the price of Bitcoin once when the graph begins its execution. We then divide 1 million by the current price of Bitcoin using a [`Divide A / B`](divide-a-b.md) block. This gives us the true amount of Bitcoin we could buy with $1 million dollars. For example, if BTC currently costs $35,000, this calculation would result in 28.57 BTC. However, we want the amount of _whole_ BTC we can afford with $1 million, which is where our `Floor` block comes in. Once we floor this value, we get 28, which is then packed into a short message using a [`Replace String In String`](../string/replace-string-in-string.md) block, and recorded in the graph's logs with a [`Print`](../log/print.md) block.&#x20;

Note that the yellow executive output on the `Get CoinGecko Coin` block is plugged directly into the `Print` block, which means that this is the next block to be called after the `Get CoinGecko Coin` block. However, for the `Print` block to execute, its "Message" parameter must be supplied with a value. This causes the `Replace String In String`block to resolve, which in turn causes the `Floor` block to resolve (which then causes the `Divide A / B` block to resolve). This is an example of implicit calling, where a non-executive block is called only when its output is required by some other block's input.
