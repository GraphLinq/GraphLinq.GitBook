# Decimal

The Decimal block in the GraphLinq IDE allows manipulation of fractional values, also known as decimal numbers. Decimal numbers are used to represent values with a higher precision than whole numbers (integers). They are essential for performing calculations that involve fractional parts.

### Input Parameters

The Decimal block does not have any inputs. Instead, it serves as a static value block that can be connected to other blocks in a graph.

### Output

The Decimal block has one output parameter that represents the decimal value. This output can be connected to other blocks that accept decimal values as input.

### Usage

The Decimal block is used in various mathematical operations within a graph. It can represent quantities like currency, measurements, and percentages accurately. Additionally, the Decimal block is often used in conjunction with other math blocks to perform complex arithmetic calculations.

### Examples

#### Performing Arithmetic Operations

Suppose a graph needs to calculate the total cost of items in a shopping cart, including tax. The graph may use Decimal blocks to represent the item prices, tax rate, and the total cost.

**Input (Decimal):**

```
Item Price: $10.99
Tax Rate: 0.08 (8%)
```

By connecting the Decimal blocks to an Add A + B block, the graph can calculate the total cost, including tax.

**Output (Decimal):**

```
Total Cost: $11.87
```

#### Handeling Financial Transactions

In a financial application, the Decimal block can be used to represent currency values accurately. For example, a graph could calculate the interest accrued on a loan using decimal values for principal amount, interest rate, and time.

**Input (Decimal):**

```
Principal Amount: $1000.00
Interest Rate: 0.05 (5%)
Time: 2 years
```

By connecting the Decimal blocks to a Multiply A \* B block and a Multiply A \* B block, the graph can calculate the total interest and the final amount.

**Output (Decimal):**

```
Total Interest: $100.00
Final Amount: $1100.00
```

_Note:_ The Decimal block is a versatile tool for working with fractional values and performing precise calculations. By using Decimal blocks in combination with other math blocks, developers can build graphs that handle various financial, scientific, and engineering calculations with accuracy and efficiency.



***

### More Information

The Decimal block in the GraphLinq IDE allows users to enter fractional values or non-integers into their graphs. These values are represented as 64-bit floating-point numbers. The Decimal block's output can be linked to the decimal type input of other blocks, enabling the use of decimal values in various calculations and operations.

<figure><img src="https://i.imgur.com/m46Z2D5.png" alt=""><figcaption></figcaption></figure>

```
Decimal: 1.20

Limit Order:
  - Exchange: Binance
  - Pair: ADA/USDT
  - Order Type: Limit
  - Quantity: 200 ADA
  - Limit Price: (Decimal)
```

In the example above, we have a Decimal block with the value 1.20, representing the limit price of $1.20 USDT. This Decimal value is then connected to the "Limit Price" input of the Limit Order block. When the graph is executed, it will place a limit order on the Binance exchange for 200 ADA if the price of ADA reaches or goes below $1.20 USDT.

The Decimal block is useful for setting precise numerical values that may involve fractional amounts or non-integer quantities. Additionally, like other base variable data types in GraphLinq, decimal values can be saved as persistent variables using Set Variable blocks and retrieved later using Get Variable blocks. This enables users to dynamically adjust and update decimal values within their graphs based on real-time data or calculations.&#x20;

As with all the other base variable data types, we can also save decimal values determined at runtime as persistent variables using [`Set variable`](set-variable.md) blocks, and we can retrieve those values later using [`Get variable`](get-variable.md) blocks.\
