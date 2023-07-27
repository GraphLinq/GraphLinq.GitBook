# Variable Type

The variable is the node type that save context data in the graph context memory, basically you can save the data you want inside it and retrieve them later on to transform them or use them on other nodes (with `SetVariable`, `GetVariable` function type)

Current deployed variable type list over the Engine network:

```
"Block Type" -> "NodeBlock.Engine.Nodes.BoolNode"
"Description" -> "In computer science, the Boolean data type is a data type that has one of two possible values (usually denoted true and false) which is intended to represent the two truth values of logic and Boolean algebra"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.DecimalNode"
"Description" -> "The decimal data type is an exact numeric data type defined by its precision (total number of digits) and scale (number of digits to the right of the decimal point). ... Scale can be 0 (no digits to the right of the decimal point)."
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.IntNode"
"Description" -> "An integer format is a data type in computer programming. ... Integers represent whole units. Integers occupy less space in memory, but this space-saving feature limits the magnitude of the integer that can be stored."
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.LongNode"
"Description" -> "The long data type is a 64-bit two's complement integer. The signed long has a minimum value of -263 and a maximum value of 263-1."
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.StringNode"
"Description" -> "A string is a data type used in programming, such as an integer and floating point unit, but is used to represent text rather than numbers. It is comprised of a set of characters that can also contain spaces and numbers."
"Block Gas Cost" -> 0
```
