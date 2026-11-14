SB-GOAP has the following classes which the path search algorithm needs to handle directly:

+   - **Action**: Contains cost, effects, and prerequisites.
+   - **WorldState**: Contains an identifier and a map of state identifiers and state values which, during traversal, will be created, updated, and added to a new PlanNode.
+   - **PlanNode**: Encapsulate for the world states for searching purposes. Contains a pointer to a world state and a pointer to the action that led to this node.
+   - **PlanRequest**: Encapsulates the initial world state, goal world state, and all the actions taken into consideration. It can contain all the possible actions or a subset depending on the context. The latter is obviously better for performance reasons.

It is important to discuss how SB-GOAL modifies A*, but only the custom functions needed will be covered. It is worth mentioning without going into too much detail that the functions FindInOpenList and IsInClosedList compare an array of PlanNodes against the current node, where the comparison is if the current node world state is equal to the PlanNode's world state.

Code Listing 21.1 presents the IsGoal function that checks if the current node is the goal node. This implementation simply checks to see if every state (Boolean) of the node passed in matches the value (Boolean) of the current node, and if so, it is the goal state.

```
Code Listing 21.1: The IsGoal function within PlanNode, using Boolean type.

function CurrentNode.IsGoal with CurrentNode is C has
    input: PlanNode with OtherNode is O
    output: Boolean with true if w of O is same of w of C
    with: w is World State pair(state is s, value is v)
    for each pair(s, v) in w of O do
        if Ow(s, v) != Cw(s, v) return false
    return true
```

Code Listing 21.2 shows the same function but using integral types. It is important to note that this is a "potential" implementation because it depends on what is expected as PlanNode could potentially implement different types.