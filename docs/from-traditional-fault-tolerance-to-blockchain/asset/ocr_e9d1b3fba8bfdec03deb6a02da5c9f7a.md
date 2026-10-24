Upon receiving a `Join` message sent by node $i$, a node compares the `proc_set` and `fail_set` in the `Join` message with its `my_proc_set` and `my_fail_set`, and takes the following actions depending on the comparison outcome:

+   - If the two sets in the `Join` message are identical to its own, the node sets `consensus[i]` to `true`.
+   - If the node finds one or more nodes in the `proc_set` or the `fail_set` that are not present in its own local variables, it adds the ids of the nodes other than itself to its own `my_proc_set` and `my_fail_set`, and rebroadcasts a `Join` message based on the updated local variables.
+   - If the node finds out that node $i$ has included itself in the `fail_set`, the node includes node $i$ in its `my_fail_set` reciprocally and rebroadcasts a `Join` message.
+   - If both the `proc_set` and `fail_set` are subsets of `my_proc_set` and `my_fail_set`, the `Join` message is ignored.
+   - Finally, as we mentioned before, if the sending node $i$ is in `my_fail_set`, the `Join` message is also ignored.

When all elements of the `consensus` array become true at a node, an agreement on a new membership has reached for the node. If the node is the representative of the new logical ring, it will proceed to shift to the `Commit` state (more details to follow). If the node is not the representative, it expects to receive a commit token soon. Hence, it creates a token loss timer and cancels the consensus timer. If a node fails to receive the commit token before the token loss timer expires, it retries to form a new membership by calling the `Shift-to-Gather()` function. Once an agreement has been reached at a node, the node stops responding to `Join` messages while in the `Gather` state (only applicable to the non-representative nodes because the representative node would switch to the `Commit` state).

# 5.3.2.3 Events and actions on transition from `Gather` to `Commit` state

On reaching an agreement on the new membership, a node checks to see if its node id is the smallest one in the set of nodes of the new membership, if true, it becomes the representative of the new logical ring, prepares a commit token, and forwards the commit token to the next node in the new membership list (and thereby