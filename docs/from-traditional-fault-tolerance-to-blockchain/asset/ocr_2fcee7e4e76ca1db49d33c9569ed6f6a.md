Assuming that there has been a unique coordinator since the server is turned on, the first time a fast round is run will always allow the coordinator to send an *any* message in phase 2. In a typical state-machine replicated system, this would allow the running of a single phase 2a message for all instances of Fast Paxos, which would eliminate one communication step, as shown in Figure 6.13. This is the sole advantage of Fast Paxos, hence, whenever possible, a fast round is run and a classic round is used only when a consensus cannot be reached in the fast round due to the failure of the coordinator or due to a collision.

![](bbox=[0.22, 0.32, 0.78, 0.52])

Figure 6.13 Normal operation of (Multi-) Fast Paxos in a client-server system.

# 6.5.2 Collision Recovery, Quorum Requirement, and Value Selection Rule

In this subsection, we elaborate on the issues that we have ignored so far, including collision recovery, quorum requirement, and value selection rules. All these issues are rooted at the possible collision in a fast round.

During a fast round, if the coordinator issues an *any* phase 2a message, the acceptors would have freedom to select its only values. If there are several clients proposing different values concurrently (*i.e.*, they issue requests to the server replicas concurrently), it is likely that different acceptors could select different values, which would cause a collision. When this happens, the coordinator might see different values in the quorum of votes it has collected, which would prevent the consensus from being accomplished in this fast round.