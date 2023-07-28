# Add A + B

Add A + B

The Add A + B block is a fundamental component in the GraphLinq IDE, designed to calculate the sum of two numeric values, A and B. This block takes two inputs, "A" and "B," and efficiently computes their sum. The output of this operation is the numerical result of adding A and B together.

Block Details: Add A + B blocks have two input parameters: "A" and "B." These input parameters can accept various types of numeric data, such as decimal, integer, or long. Additionally, "A" and "B" can have different data types, enabling users to add a decimal value to an integer value or vice versa.

Execution: Similar to other block types in the Math category, Add A + B blocks are non-executive blocks. They do not have yellow connectors, which means they are not explicitly called by other blocks and cannot call other blocks themselves. Instead, they are implicitly called whenever their output is required as input by some other executing block.

Use Case: The Add A + B block finds extensive applications in various domains where numerical addition is necessary. It is commonly used in financial calculations, data analysis, and general arithmetic operations. For instance, in financial applications, this block can be used to calculate total investment amounts, revenue projections, or asset valuations.

Example: Let's consider an example to demonstrate the functionality of the Add A + B block. Suppose we have a graph that calculates the total sales revenue for a business. The graph takes inputs "A" and "B," representing the revenue from two different product lines. The Add A + B block then computes the total revenue by adding the revenue from both product lines together.

The output of the Add A + B block represents the overall sales revenue, which can be further processed or displayed using other blocks in the graph. The graph can be configured to update in real-time, allowing business owners to monitor their total revenue dynamically as it changes.

This example illustrates the implicit calling of the Add A + B block, as it is executed only when its output is required by another block's input. By utilizing the Add A + B block, developers can perform efficient addition operations within their graphs, making it easier to perform complex calculations and data processing tasks.

The versatility of the Add A + B block makes it an indispensable tool for developers seeking to perform mathematical computations within their graphs. Whether it's summing financial data, calculating statistical measures, or performing general arithmetic operations, the Add A + B block offers a straightforward and effective solution for adding numerical values together.







`Add A + B` blocks, as the name suggests, simply add two given numbers together and then output the result.

`Add A + B` blocks have two input parameters called "A" and "B". These are, of course, the two numbers we want to add together. Note that these input parameters can be supplied with any type of numeric data (decimal, integer, long), and the two data types do not need to match (ie: you can add a decimal value to an integer value).

As with all block types in the [`Math`](./) category, `Add A + B` blocks are non-executive blocks, which means that they have no yellow connectors, and thus they are never called explicitly by other blocks, and they themselves cannot call other blocks. Instead, they are called implicitly whenever their output is required as input by some other block that is executing. We can observe this happening in the example below.

<figure><img src="https://i.imgur.com/dyKrGwA.png" alt=""><figcaption></figcaption></figure>

In the example above, we use a `Get Wallet Informations` block to access information about a specific bitcoin wallet one time when the graph starts. We then use our `Add A + B` block to add together the total amount received and the total amount sent by this wallet, in order to calculate the total transaction volume across this wallet's history. Finally, we build a little output message containing this result using a [`Replace String In String`](../string/replace-string-in-string.md)block. and then print it into our graph's logs using a [`Print`](../log/print.md) block.

Note that the yellow executive output on the `Get Wallet Informations` block is plugged directly into the `Print` block, which means that this is the next block to be called after the `Get Wallet Informations` block. However, for the `Print` block to execute, its "Message" parameter must be supplied with a value. This causes the `Replace String In String` block to resolve, which in turn causes the `Add A + B` block to resolve. This is an example of implicit calling, where a non-executive block is called only when its output is required by some other block's input.

In our example, we simply calculate and then print the wallet's transaction volume one time, right when the graph starts running. It is easy to imagine a more fleshed-out and realistic example in which this calculation is done whenever requested by users on some platform like Discord or Telegram.

\
