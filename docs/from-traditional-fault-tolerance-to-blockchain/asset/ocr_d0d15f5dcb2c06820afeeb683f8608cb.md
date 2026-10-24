receive r1 ahead of r2, and thus vote to order r1 in this round. Replica 2 and replica 3 receive r2 ahead of r1, and thus vote to order r2 in this round.

The coordinator (i.e., the primary) finds two different values (2 r1 and 1 r2) in the quorum of votes it has collected. Hence, a collision is detected. The coordinator subsequently starts a new classic round to recover from the collision. According to the value selection rule introduced earlier, the coordinator chooses r1 and include the value in its phase 2a message. When a quorum of replicas has voted, r1 is chosen and the coordinator informs the other replicas, after which, the request r1 is executed and the corresponding reply is returned.

As we can see in this example, the presence of a common value from the majority of the votes (r1 in our example) does not necessarily mean that the value has been chosen in an earlier round.

![](bbox=[0.26, 0.44, 0.74, 0.86])

Figure 6.14 Collision recovery in an example system.