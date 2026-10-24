# 4.4.1.1 CA System

A CA system sacrifices partition tolerance for consistency and availability. This implies that the network partitioning fault is excluded from the fault model used in the system design. This type of systems can only be used in an environment that the network partitioning fault rarely happens, for example, a local area network or as big as a data center. Systems designed to achieve pessimistic replication are often CA systems.

# 4.4.1.2 CP System

Based on our previous argument, we cannot build a system that ensures strong consistency while tolerating all forms of network partitioning faults because it is bound that some replicas would not be able to reach other replicas by the definition of network partitioning. However, a CP system is possible under the following conditions:

+   - Consistency is achieved by a quorum-based algorithm. That is, as long as the majority of the replicas agree with each other, the system is considered consistent.
+   - The network partitioning fault results in a partition that consists of the majority of the replicas in the system.

In such a CP system, the replicas residing in the majority partition would proceed as usual (i.e., as if there is no network partitioning fault), while the replicas in the minor partition (or partitions) would stop operating, hence losing the availability property. A number of partition-tolerant group communication systems [3, 20] are CP systems.

# 4.4.1.3 PA System

Many new cloud computing systems [1, 23], as well as systems that employ optimistic replication [25], are designed to ensure PA. As we discussed in section 4.3, the loss of consistency is only temporary - the replica states will eventually converge when the network partitions merge and when the system is quiescent.

# 4.4.2 Implications of Enabling Partition Tolerance

For a PA system, it should strive to detect and reconcile any consistency because users do expect eventual consistency even if