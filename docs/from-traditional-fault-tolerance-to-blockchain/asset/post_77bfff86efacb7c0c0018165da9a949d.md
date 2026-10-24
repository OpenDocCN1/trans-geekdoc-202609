
### 4.3.5.2 Timestamp Matrix

For systems that use timestamp matrices, they can learn the stable operations without any additional message exchanges. At site \(i\), a cell in its timestamp matrix, \(TM_i[j][k] = t\), means that according to site \(i\)’s conservative estimate, site \(j\) has received all operations originated from site \(k\) up to \(t\). Hence, to find out what operations from site \(k\) that have become stable, all we need is to take the minimum of all rows at element \(k\), i.e., if \(min(TM_i[0][k], TM_i[1][k], ..., TM_i[N-1][k]) = t\), all sites have received the first \(t\) operations submitted at site \(k\).

![](img/7320b1480d74f1d65f74659cab456782_166_0.png)

Figure 4.16 Update commit using timestamp matrices in a system with three replicas.

Consider a system shown in Figure 4.16. Site A’s timestamp matrix is:

| 3 | 1 | 0 |
|---|---|---|
| 2 | 1 | 0 |
| 0 | 0 | 0 |

Site B's timestamp matrix is:

| 2 | 1 | 0 |
|---|---|---|
| 2 | 1 | 2 |
| 2 | 1 | 2 |

Site C's timestamp matrix is the same as that of site B:

| 2 | 1 | 0 |
|---|---|---|
| 2 | 1 | 2 |
| 2 | 1 | 2 |

It is apparent that site A cannot garbage collect any operation because the third row in its timestamp matrix is (0, 0, 0). For site B, the minimum of the first column (corresponding to the status of site A) is 2, the minimum of the second column (corresponding to the status of site B) is 1, and the minimum of the third column (corresponding to the status of site C) is 0. Then, site B can safely garbage collect the first two operations from site A: O_A1 and O_A2, and the first operation from site B itself: O_B1. Similarly, site C can safely purge the three operations as well.

Even though the effectiveness of using timestamp matrices for update commit also depends on good connectivity of different sites, a site that has few or no operations submitted would not prevent other sites from committing updates and performing garbage collection.

## 4.4 CAP Theorem

The CAP theorem was introduced by Eric Brewer in 2000 [6] regarding what can be achieved in a practical distributed system. The theorem states that it is impossible to satisfy all three of the following guarantees:

- Consistency (C): the replicated data is always consistent with each other.
- Availability (A): the data is highly available to the users.
- Partition tolerance (P): the system can continue providing services to its users even when the network partitions.

The proof of the CAP theorem is straightforward [11] because in the presence of network partitions, replicas in different partitions could not communicate with each other. If the designer of a system favors replica consistency, then the availability may have to be sacrificed. Similarly, if the designer chooses to ensure high availability, there is no way strong consistency among the replicas in different partitions can be achieved — the replicas cannot communicate!

### EXAMPLE 4.8

Similar to [11], we consider a network with only two nodes N1, N2. Assume that a network partitioning fault occurs and it isolates node N1 from node N2. We further assume that we are going to ensure P and A, which means the following could happen:

- A client that could reach N1 issues an update W1. The update is immediately applied at N1. Due to the network partitioning fault, N2 is not aware of the update W1 at N1.
- Another client that could reach N2 also issues an update W2. The update is immediately applied at N2. Due to the network partitioning fault, N1 is not aware of the update W2 at N2.
- It is apparent that the states of N1 and N2 have become inconsistent from now on.

Note that the states of the two nodes would become inconsistent only after different updates have applied at them. If one is an update operation W and the other is a read-only operation R, we cannot conclude that the states have become inconsistent. Indeed, even if the operation R on N2 is issued significantly after the operation W on N1 in real time, it does not necessarily mean that R is causally related to W and we should expect R to read the value written by W. Without some out-of-band channel that links the two operations, it is perfectly legal for R to read a value prior to the update operation W. If the system is repaired from the network partitioning fault, N1 and N2 could easily merge their history so that all operations are serializable (e.g., R would be ordered prior to W after N1 transfers its state or operations to N2).

Since its inception, the CAP theorem has attracted extensive attention and debates [1, 4, 7, 12, 23]. The CAP theorem highlighted the need to strike a good balance between consistency and availability in the presence of network partitioning faults when designing practical systems because many systems might face network partitioning faults [7]. Much debate lies on the reason for the use of reduced consistency models in favor of high availability. As we have seen in the previous section on optimistic replication and rightly pointed out by a number of researchers [1], the adoption of reduced consistency models is often not due to concerns of network partitioning faults, but for better performance for applications running over wide-area networks.

Furthermore, the definitions of C, A, and P are quite unclear. For example, does requiring C mean that all non-faulty replicas must be in sync all the time? On the other hand, if a quorum-based consensus algorithm (such as Paxos [18]) is used to coordinate the replicas, the system would make progress as long as the majority of the replicas agree with each other and it is possible that the minority of replicas lag significantly behind or are in a confused state depending on the fault model used in the system. Can we call such a system as guaranteeing C? We probably should say that it does guarantee C based on common sense.

Whether or not a system guaranteeing A depends on the fault model used. For example, a system that provides high availability with a crash-fault-only model might not be able to ensure high availability in the presence of network partitioning faults or malicious faults. Without clarifying the fault model used, the scopes of availability and partition-tolerance would appear to overlap with each other:

- Partition tolerance implies that the system could ensure liveness in the presence of network partition faults.
- High availability, on the other hand, would require the tolerance of all types of faults, including network partition faults, *without specific qualification on the fault model used*.

In addition, the definition of A is vague. If the data is said to be available for a user, how long does the user have to wait for its request to be serviced? What is the relationship between A and the end-to-end latency (L) as experienced by a user? A is not absolute and neither is L. In [1], A and L are treated as different properties of a system, and thus, a PACELC model is proposed to replace CAP in system design: If there is a network partition fault, how to balance the availability and consistency (A and C); else (E), during normal operation with a fully-connected network, how to balance the requirements on latency (L) and consistency (C)?

The meaning of partition tolerance is also unclear. First, what is considered as a network partitioning fault can be confusing. A straightforward interpretation of a network partitioning fault is that the network is partitioned into several disjoint partitions due to a fault at a router/switch or a communication link. However, normally there is no way for a replica to have such global knowledge and different replicas may have completely different views regarding whether or not the network has partitioned. If a replica could reach every node that it needs to communicate, then to its view, there is no network partitioning fault, even though the network has already been partitioned and that replica together with all other nodes it communicates with reside in one of the partitions. Further, a replica could only detect a network partitioning fault by using a timeout when communicating with other nodes. To a replica, a network partitioning fault has happened if it has timed out a request issued on another node. That is why a network partitioning fault is often modeled as a message loss [11]. Obviously, if a network partitions and quickly recovers before the timeout, the partitioning fault might have no impact on the system.

### 4.4.1 2 out 3

The CAP theorem dictates that at the best, we could design a system that achieves 2 out of 3 properties, that is, a system that either ensures CA, CP, or PA, but not all three CAP, as shown in Figure 4.17.

![](img/7320b1480d74f1d65f74659cab456782_170_0.png)

Figure 4.17 An illustration of the CAP theorem.
