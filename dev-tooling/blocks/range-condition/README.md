# Range Condition

The Range Condition category in the GraphLinq IDE encompasses blocks that facilitate range-based conditional branching. These blocks enable developers to determine whether a numeric value falls within a specific range and execute different paths accordingly.

### Decimal Range Branch

The Decimal Range Branch block is a fundamental component within the Range Condition category. It allows developers to define a range of decimal values and test whether a given decimal value lies within that range.

This block has three main inputs: "Value," "Lower Bound," and "Upper Bound." The "Value" input represents the decimal value that will be evaluated, while the "Lower Bound" and "Upper Bound" inputs define the range.

The behavior of the Decimal Range Branch block is as follows:

* If the "Value" is greater than or equal to the "Lower Bound" and less than or equal to the "Upper Bound," the graph will follow the path connected to the "Within Range" output.
* If the "Value" is outside the defined range, the graph will follow the path connected to the "Outside Range" output.

### Example

In this example, we use the Decimal Range Branch block to check whether the temperature value falls within the "Comfortable Range." If the temperature is within the range of 20 to 25 degrees Celsius, the graph will execute the nodes connected to the "Within Range" output, indicating that the temperature is comfortable. If the temperature is below 20 or above 25 degrees Celsius, the graph will follow the nodes connected to the "Outside Range" output, allowing for handling scenarios where the temperature is too cold or too hot.

The Decimal Range Branch block enables developers to implement sophisticated range-based conditions in their graphs. By defining specific ranges for numeric values, developers can create dynamic applications that adapt to varying data inputs. This category provides a powerful tool for designing conditional branches based on decimal ranges, making GraphLinq graphs capable of handling a wide range of scenarios with precision and accuracy.
