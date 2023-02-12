# Condition Type

The condition is the node type that offers a way to do different paths of execution regarding value of node results or specified pre-set variables.

Current deployed condition type list over the Engine network:

```
"Block Type" -> "NodeBlock.Engine.Nodes.Vars.IsVariableExist"
"Description" -> "Check if a variable exist in the graph memory context"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.Text.StringContainsNode"
"Description" -> "Check if a string contains a other string"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.Branch.BoolBranchNode"
"Description" -> "Trigger different node path on a condition based on a bool variable value state (true/false)."
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.Branch.DecimalBranch"
"Description" -> "Trigger different node path on a condition based on a decimal variable value state (equals to, greater or equals, lower then, lower or equals..)."
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.Branch.DecimalRangeBranch"
"Description" -> "Trigger a condition of a node execution based over a range of values (included in a min or max number)"
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.Branch.IntBranchNode"
"Description" -> "Trigger different node path on a condition based on an integer variable value state (equals to, greater or equals, lower then, lower or equals..)."
"Block Gas Cost" -> 0
```

```
"Block Type" -> "NodeBlock.Engine.Nodes.Branch.StringBranchNode"
"Description" -> "Trigger a condition over two string value to compare if their are equals to each other"
"Block Gas Cost" -> 0
```
