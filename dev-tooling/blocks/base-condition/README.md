# Base Condition

This block category comprises four block types that are used to determine a graph's executive flow (which yellow connection will fire next). They are: [`Boolean Branch`](boolean-branch.md), [`Decimal Branch`](decimal-branch.md), [`Integer Branch`](integer-branch.md), and [`String Branch`](string-branch.md).&#x20;

A `Boolean Branch` block takes a boolean value as input, and fires one of two yellow outputs depending on the value of the boolean.

A `Decimal Branch` block takes two decimals as input, and has different yellow outputs for all the following scenarios: the first number is greater than the second, the first number is greater than or equal to the second, the two numbers are equal, the first number is less than or equal to the second, and the first number is less than the second.

An `Integer Branch` block works the same way as a `Decimal Branch` block, except that the two input numbers must be integers rather than decimals.

A `String Branch` block takes two strings as input, and fires one of two yellow outputs depending upon whether the two strings are identical or not.\
