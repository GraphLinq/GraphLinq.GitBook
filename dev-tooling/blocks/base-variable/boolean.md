# Boolean

The `Boolean` block allows us to to enter boolean values ("true" or "false") to be used as conditions to determine execution flow (which yellow line we'll be following next).

The simplest way to use a boolean value to control flow is with the help of a [`Boolean Branch`](../base-condition/boolean-branch.md) block, which takes a boolean as input, and executes one of two output connections depending on the value of the boolean, as seen here:

<figure><img src="https://i.imgur.com/cD6prkM.png" alt=""><figcaption></figcaption></figure>

In the above example, "true" has been typed into the `Boolean` block, which is then being sent as the input data into the [`Boolean Branch`](../base-condition/boolean-branch.md) block. When the [`Boolean Branch`](../base-condition/boolean-branch.md)block is run, it will trigger the top yellow connection to fire next, since that output corresponds with the "true" value it received as input. Therefore, the topmost [`Print`](../log/print.md) block would execute, and we would see "the boolean was true" in our logs.

The example above, while very simple, is not very realistic, because no matter what, the top output of the [`Boolean Branch`](../base-condition/boolean-branch.md) will fire every time we run this graph, since we hard-coded its condition to be simply the value "true". The `Boolean` and [`Boolean Branch`](../base-condition/boolean-branch.md) blocks in the above example are therefore pointless.

The following graph snippet is an example of a more realistic use of `Boolean` and [`Boolean Branch`](../base-condition/boolean-branch.md) blocks:

<figure><img src="https://i.imgur.com/dANtgmV.png" alt=""><figcaption></figcaption></figure>

In this example, we are using a [`String Branch`](../base-condition/string-branch.md) block to check if two given strings are equal. If they are equal, it triggers the top [`Set variable`](set-variable.md) block, which uses a `Boolean`block to assign the value "true" to a variable called "theStringsMatch" (if a variable by that name doesn't exist yet, then this will also declare a variable by that name). If the two strings are not the same, it instead executes the bottom [`Set variable`](set-variable.md) block, which assigns the value "false" to the same variable.

Later, in the right side of the image, we can see an example of that same boolean variable being accessed with a [`Get variable`](get-variable.md) block, and the value of that variable is then used as the input to a [`Boolean Branch`](../base-condition/boolean-branch.md) block, which will determine which of its outputs will be executed.This is an example of controlling the flow of our graph using a boolean variable whose value is not known to the developer when they make the graph, but is instead calculated only once the graph is running.&#x20;

Note: the values for `Boolean` blocks are not case-sensitive, so they work with "true", "True", "false", and "False". If you were to type anything besides those values into the `Boolean` block above, then neither of the [`Boolean Branch`](../base-condition/boolean-branch.md) outputs would execute.

\
