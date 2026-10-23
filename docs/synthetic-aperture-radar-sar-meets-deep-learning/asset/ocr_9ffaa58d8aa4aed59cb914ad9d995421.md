so it requires 3 TX2s to collaborate the training process of one mini-batch. The two sets of candidate partition points calculated by CWB are {p2, p3, p4, p5} and {p7, p8, p9, p10}, satisfying that the training of each partition can be carried out on a single TX2, the rest of the partition points have been screened out. CWB then performed time equalization utilizing the data in shown Figure 13c, by accumulating the forward and backward latency of individual layers under different candidate partition points, to obtain the running time of each TX2 node during a training batch.

As shown in Figure 14, CWB used the equipment utilization index to find the optimal partition point among the candidate partition points. Figure 14a shows the runtime proportion of each node under candidate partition points, the transmission latency varies depending on different combinations of partition points. In Figure 14b CWB found the partition point combination with the highest equipment utilization {p3, p8}, representing the optimal partition points. For the given Lite-SRL network structure and training settings, CWB partitioned it into the following three parts: partition 1 {p1, p2}, partition 2 {p3, p4, p5, p6, p7}, partition 3 {p8, ⋯ p28}.

# 6.2. Distributed Training with Higher Efficiency

We used six TX2 nodes to compose an on-board computation platform and tested the proposed distributed training baseline along with the improved dynamic chain system. In our on-board distributed training baseline experiments, six nodes formed a two-chain hybrid parallel training according to Figure 4b. After the workload balancing, we allocated the training of three network partitions to TX2 nodes on each chain. In dynamic chain system experiments, three nodes are responsible for the computation of partition 1, two for the computation of partition 2, and one for the computation of partition 3 of the model, as shown in Figure 4b. The two distributed training methods were performed 1000 iterations each, the distributed training system performed parameter aggregation every 100 iterations and updated the model parameters in each node using the aggregated parameters. Here one iteration referred to the completion of one mini-batch's forward and backward propagation.

As shown in Tables 5 and 6, the average runtime of executing one iteration in the baseline is 3572 s, while the average time in dynamic chain system is 2750 s.

Table 5. Distributed training baseline.

| Average Running Time of One Iteration (ms) | Partition 1 | Partition 2 | Partition 3 |
|---|---|---|---|---|---|---|
|  | Node 1 | Node 2 | Node 3 | Node 4 | Node 5 | Node 6 |
| Baseline 3572 | Average runtime of each node in one iteration (ms) |  |  |  |  | |
|  | 1035 | 1039 | 1145 | 1139 | 921 | 923 |
|  | Running iterations |  |  |  |  | |
|  | 500 | 500 | 500 | 500 | 500 | 500 |

Table 6. Improved dynamic chain system.

| Average Running Time of One Iteration (ms) | Partition 1 | Partition 2 | Partition 3 |
|---|---|---|---|---|---|---|
|  | Node 1 | Node 2 | Node 3 | Node 4 | Node 5 | Node 6 |
| Dynamic 2750 | Average runtime of each node in one iteration (ms) |  |  |  |  | |
|  | 1036 | 1038 | 1037 | 1140 | 1142 | 922 |
|  | Running iterations |  |  |  |  | |
|  | 329 | 331 | 340 | 406 | 594 | 1000 |

The baseline used 6 nodes to complete 1000 iterations of training in 3572 s, and the 2 chains had each been running for 500 iterations. In comparison, the dynamic chain system used the same nodes to complete 1000 iterations of training in 2750 s. With the scheduling of the communication module, the system can be viewed as containing 3 chains; the nodes responsible for the first and second partitions end up with different running iterations, and