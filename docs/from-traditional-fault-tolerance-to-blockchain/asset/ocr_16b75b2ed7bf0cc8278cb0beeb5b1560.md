with two competing originators that timed out Node1 concurrently. As shown in Figure 5.5, Node2 and Node4 concurrently initiated a membership view change by broadcasting an invitation for a new view (referred to as VIEW-CHANGE in the figure). Node3 receives the invitation sent by Node2 first and accepts it. Hence, when Node4's invitation arrives, Node3 rejects it and responds with a no message. Similarly, Node5 receives and accepts the invitation sent by Node4 first, and rejects the invitation sent by Node2. Hence, both Node2 and Node4 would decide to abort their rounds of membership view change and wait for a random amount time before they each would initiate a new round of membership view change.

Node4 completes the random wait first and broadcast a new round of membership view change invitation. This time, the invitation arrives at Node2 before the node completes its random wait. Node2 terminates its random wait upon receiving the invitation from Node4, accepts the invitation, and responds with a YES message. Consequently, Node4 is able to collect positive responses from Node2, Node3, and Node4, and proceed to commit to the new view.

![](bbox=[0.23, 0.525, 0.77, 0.755])

Figure 5.6 Membership change scenario: premature timeout.

# EXAMPLE 5.3

Premature timeout. Due to the asynchrony of the system, a node might timeout the sequencer prematurely and initiate a membership view change. This scenario is shown in Figure 5.6,