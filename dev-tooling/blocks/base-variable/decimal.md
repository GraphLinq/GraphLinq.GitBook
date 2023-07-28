# Decimal

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
