
Note that after one pass of the message flow, the maximum value of `P(x)` has been obtained. However, one is also interested in knowing the corresponding value `x*`, for which the maximum occurs, that is,

```
x* = argmax_x P(x).
```

This is achieved by a reverse message passing process, which is slightly different from what we have discussed so far, and it is known as back-tracking.

**Back-tracking**: Assume that `x1` is the chosen node to play the role of the root, where the flow of messages “converges.” From Eq. [(15.61)](#Chp015_755-803_B9780443292385000214.xhtml#deq87), we get

```
x1* = argmax_x1 μ_fa→x1(x1) μ_fg→x1(x1) μ_fh→x1(x1).
```
(15.67)

A new message passing flow now starts, and the root node, `x1`, passes the obtained optimal value to the factor nodes to which it is connected. Let us follow this message passing flow within the nodes of the subtree `T[A]`.

*   **Node A**: It receives `x1*` from node `x1`.

    1.  **Selection of the optimal values**: Recall that
