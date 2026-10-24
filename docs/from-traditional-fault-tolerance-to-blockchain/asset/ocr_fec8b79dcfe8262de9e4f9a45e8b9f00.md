for the commit token after they finds that an agreement on the membership has reached. When a node receives the commit token the first time, it fills the entry corresponding to itself in the commit token, forwards the token to the next node, and enters the `Commit` state too.

When `N2` receives the commit token the second time, it has collected all the necessary information for recovery because every node in the new logical ring has provided necessary information. Hence, `N2` updates its local variables and the commit token accordingly, forwards the token again to `N3`, and enters the `Recovery` state. An important step is to determine the view number for the new view, which the maximum view number in the `Join` messages plus 4. `N2` also writes the view number to stable storage. When `N3` receives the commit token the second time, it performs similar steps as `N2`, and forwards the commit token to `N4`. Similarly, `N4` forwards the token to `N5`. `N5` in turn will forward the token back to `N2`.

Note that even though we have assumed that `N2` times out `N1` first, the view change will still be successful if two or more nodes time out `N1` concurrently and send `Join` messages as long as they all use the same `proc_set` and `fail_set`.

![](bbox=[0.253, 0.563, 0.842, 0.856])

# Figure 5.10 Membership changes due to a premature timeout by N2.