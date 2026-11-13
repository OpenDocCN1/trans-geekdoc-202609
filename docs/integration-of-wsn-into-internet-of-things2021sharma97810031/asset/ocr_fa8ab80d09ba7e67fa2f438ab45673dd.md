![](bbox=[0.17, 0.09, 0.83, 0.34])

FIGURE 6.16 End-to-end delay of different routing protocols with varying number of nodes.

# 6.7 CONCLUSION

In this chapter, we present different routing algorithms. Based on the performance metrics that has been simulated over ns2 simulator, it has been observed that AODV that is a reactive protocol has some additional features over DSDV by minimizing the number of broadcast messages that are created based on demand. AODV performs better than DSDV, which is based on a table-driven approach where each node maintains information in the routing table about neighboring nodes, and DSR, which is a type of protocol where the route is discovered on demand, that is, on the basis of demand for any particular node, the node initiates route discovery mechanism. AODV results in a less end-to-end delay between the packets and maximum throughput. The routing protocols suffer from a number of limitations: the network's complexity increases on increasing the number of nodes, link failures, etc. Therefore, different optimization techniques were used to find the shortest path between the sources and their destination. Here, two optimization techniques—ACO and swarm intelligence-based optimization—have been studied. The ACO technique is influenced by real ant colonies. This is used for searching problems in telecommunications such as routing; this also solves problems of routing in MANETs. In a network, ACO techniques found the best-suited path between the two nodes, which is employed as input for particle swarm optimization techniques. In the future, the work can be extended by using different probabilistic modeling techniques.

# REFERENCES

+   1. Lee, S., & Kim, S. B. (2019). Parallel simulated annealing with a greedy algorithm for Bayesian network structure learning. IEEE Transactions on Knowledge and Data Engineering. doi:10.1109/tkde.2019.2899096.

+   2. Mokube, I., & Adams, M. (2007). Honeypots: Concepts, approaches, and challenges. In Proceedings of the 45th Annual Southeast Regional Conference. New York, USA: ACM, pp. 321–326.