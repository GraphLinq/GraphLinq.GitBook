# Base Variable

This category of blocks comprises block types that correspond to all the basic data types in computer science: [`Boolean`](boolean.md), [`Decimal`](decimal.md), [`Integer`](integer.md), [`Long`](long.md), and [`String`](string.md). Additionally, this category contains [`Secret String`](secret-string.md) blocks, which are equivalent to [`String`](string.md) blocks in every way except that they hide their contents from whomever is viewing the graph file.

The block types listed above can be used to enter hard-coded data directly into our graphs (analgous in programming to using 'literals').

Moreover, by using the [`Set variable`](set-variable.md) block, we can declare and assign to variables in order to save data within our graph's data context. Data stored this way can be retrieved with [`Get variable`](get-variable.md) blocks.

This category also contains the [`Is Variable Exist`](is-variable-exist.md) block, which determines which path to execute based upon whether a variable by a given name has already been declared with a [`Set variable`](set-variable.md) block.

Finally, this category also contains the [`Variable Portal`](variable-portal.md) block, which allows us to pipe data from one area of our graph to another while keeping things visually tidy.\
