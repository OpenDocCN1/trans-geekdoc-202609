If there is a network partition fault, how to balance the availability and consistency (A and C); else (E), during normal operation with a fully-connected network, how to balance the requirements on latency (L) and consistency (C)?

The meaning of partition tolerance is also unclear. First, what is considered as a network partitioning fault can be confusing. A straightforward interpretation of a network partitioning fault is that the network is partitioned into several disjoint partitions due to a fault at a router/switch or a communication link. However, normally there is no way for a replica to have such global knowledge and different replicas may have completely different views regarding whether or not the network has partitioned. If a replica could reach every node that it needs to communicate, then to its view, there is no network partitioning fault, even though the network has already been partitioned and that replica together with all other nodes it communicates with reside in one of the partitions. Further, a replica could only detect a network partitioning fault by using a timeout when communicating with other nodes. To a replica, a network partitioning fault has happened if it has timed out a request issued on another node. That is why a network partitioning fault is often modeled as a message loss [11]. Obviously, if a network partitions and quickly recovers before the timeout, the partitioning fault might have no impact on the system.

# 4.4.1 2 out 3

The CAP theorem dictates that at the best, we could design a system that achieve 2 out of 3 properties, that is, a system that either ensures CA, CP, or PA, but not all three CAP, as shown in Figure 4.17.

![](bbox=[0.356, 0.723, 0.642, 0.892])

Figure 4.17 An illustration of the CAP theorem.