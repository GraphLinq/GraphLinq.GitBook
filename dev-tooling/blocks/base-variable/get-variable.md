# Get variable

`Get variable` blocks are used to retrieve the values of variables that have previously been declared and assigned to by [`Set variable`](set-variable.md) blocks.

`Get variable` blocks have one input: a string for the name of the variable we are accessing. They also have one output, which is the value of the variable we have accessed.

The purpose of `Get Variable` and [`Set variable`](set-variable.md) blocks is to be able to store data in variables that can be accessed and modified later on in a graph's execution

If no variable exists with the name that we pass to a `Get variable` block, then it will simply output no data, and any block receiving as input the `Get Variable` block's output will instead receive empty (or null) data.&#x20;

Refer to the [`Set variable`](set-variable.md) block page for examples of `Get variable` and [`Set variable`](set-variable.md) blocks in action.
