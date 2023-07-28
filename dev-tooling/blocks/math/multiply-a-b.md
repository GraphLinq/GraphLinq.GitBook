---
description: Calculate the product of two numeric values
---

# Multiply A \* B

The Multiply A \* B block in the GraphLinq IDE is a fundamental mathematical block used to calculate the product of two numeric values, A and B. This block is essential for performing various arithmetic operations and is widely used in mathematical computations and data processing tasks.

### Block Description

The Multiply A \* B block is categorized under the Math blocks in the GraphLinq IDE. It is a non-executive block, which means it does not have yellow connectors and is implicitly called when its output is required by other blocks during graph execution.

### Input Parameters

The Multiply A \* B block requires two input parameters:

1. A (Numeric Type): The A input represents the first numeric value to be multiplied.
2. B (Numeric Type): The B input is the second numeric value used for multiplication.

Both A and B inputs can accept various numeric data types, including decimals, integers, and longs. The block automatically performs type conversion if the two inputs have different numeric data types.

### Output

The Multiply A \* B block outputs the result of multiplying the values of input A and input B. The output is of the same data type as the inputs and represents the product of the multiplication.

### Example Use Case

Let's explore a practical example of how the Multiply A \* B block can be used within a graph:

1. The graph receives sensor data containing the temperature readings (A) and the number of units (B) produced in a factory.
2. The Multiply A \* B block is called, taking the temperature readings (A) as the first numeric value and the number of units produced (B) as the second numeric value.
3. The block calculates the total energy consumption by multiplying the temperature readings with the number of units produced.
4. The output represents the total energy consumed during the production process.

In this example, the Multiply A \* B block helps calculate the total energy consumption based on temperature and production quantity, providing valuable insights into the energy efficiency of the factory's production process.

### Conclusion

The Multiply A \* B block is a fundamental arithmetic block in the GraphLinq IDE, enabling developers to perform multiplication operations between numeric values. Its versatility makes it suitable for various mathematical computations, data processing tasks, and real-world applications. By utilizing the Multiply A \* B block, developers can efficiently calculate products and derive valuable information from numeric data within their graphs.



***



### More Information

The Multiply A \* B block in the GraphLinq IDE is designed to perform multiplication on two given numeric values "A" and "B." This block takes two input parameters representing the operands and outputs their product as the result. The Multiply A \* B block plays a crucial role in arithmetic operations within graphs and enables developers to compute the product of two numeric values efficiently.&#x20;

#### Block Details

The Multiply A \* B block has two input parameters, "A" and "B," which represent the numeric values to be multiplied. Both "A" and "B" can be of various numeric data types, such as decimal, integer, or long. The block performs the multiplication operation on these input values and provides the product as its output.&#x20;

#### Execution

As with other block types in the Math category, the Multiply A \* B block is non-executive. It does not have yellow connectors and is implicitly called whenever its output is needed as input by other executing blocks. Whenever the Multiply A \* B block's output is required in a graph, it performs the multiplication operation on the input values "A" and "B" and delivers the product as its output.&#x20;

#### Use Case

The Multiply A \* B block finds widespread applications in various fields, including finance, engineering, and data analytics. In financial applications, it is used for calculating interest rates, profits, and asset valuations. In engineering, it is utilized in designing components with scalable dimensions or conducting simulations involving growth or decay. In data analytics, the block aids in scaling values and performing mathematical transformations on datasets.&#x20;

#### Example

Let's consider an example to illustrate the usage of the Multiply A \* B block. Suppose we have a graph that simulates a sales calculator for an online store. The graph takes the unit price of a product (A) and the quantity of the product ordered (B) as inputs and needs to calculate the total cost of the order.

To achieve this, we can use the Multiply A \* B block. By providing the unit price (A) and the quantity (B) to the Multiply A \* B block, it performs the multiplication operation and outputs the total cost of the order as the result. This enables us to quickly determine the financial impact of the purchase for both the customers and the store.

The Multiply A \* B block's capability to perform multiplication efficiently is essential in a wide range of scenarios where the product of two numeric values needs to be computed. It empowers developers to perform arithmetic calculations within their graphs seamlessly and enhances the functionality and versatility of their applications.



***

### Full Example

`Multiply A * B` blocks simply multiply two given numbers together and then output the result.

`Multiply A * B` blocks have two input parameters called "A" and "B". These are, of course, the two numbers we want to multiply together. Note that these input parameters can be supplied with any type of numeric data (decimal, integer, long), and the two data types do not need to match (ie: you can multiply a decimal value by an integer value).

As with all block types in the [`Math`](./) category, `Multiply A * B` blocks are non-executive blocks, which means that they have no yellow connectors, and thus they are never called explicitly by other blocks, and they themselves cannot call other blocks. Instead, they are called implicitly whenever their output is required as input by some other block that is executing. We can observe this happening in the example below.

<figure><img src="https://i.imgur.com/uEE7sJF.png" alt=""><figcaption></figcaption></figure>

In this example, when our graph is run, it will print the current gas price of a simple ETH transaction into the logs.

The calculation that this graph performs begins with the current price of gas in Gwei, given by the `Estimate Gas Price` block. Next, we use a `Multiply A * B` block to multiply this by 21,000, because that is how many units of gas it costs to do a simple ETH transaction. This gives of the cost of one ETH transaction in Gwei, but we want the cost of one transaction in USD. Gwei is a denomination of Ether, so we next use a [`Divide A / B`](divide-a-b.md)block to divide our price in Gwei by one billion, which converts it into the same price denominated in Ether. Finally, we use a second `Multiply A * B` block to multiply this number by the current USD price of Ether as given by the [`Get CoinGecko Coin`](../../blocks-exchange/coingecko/get-coingecko-coin.md) block, which gives us the current USD gas cost of a simple ETH transaction.

In our example, we simply calculate and then print the price of an Ether transaction one time, right when the graph starts running. It is easy to imagine a more developed and useful example in which this calculation is done whenever requested by users on some platform like Discord or Telegram.

\
