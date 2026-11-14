![](bbox=[0.16, 0.1, 0.84, 0.42])

Figure 9.17: Example of affinity propagation. Each point is colored coded by how much it wants to be an exemplar (red is the most, green is the least). This can be computed by summing up all the incoming availability messages and the self-similarity term. The darkness of the \(i \rightarrow k\) arrow reflects how much point \(i\) wants to belong to exemplar \(k\). From Figure 1 of [FD07a]. Used with kind permission of Brendan Frey.

denoted \(r_{i \rightarrow k}\), known as the responsibility. This is a measure of how much \(i\) thinks \(k\) would make a good exemplar, compared to all the other exemplars \(i\) has looked at. In addition, each factor node \(\delta_k\) sends a message to each variable node \(c_i\). Again this can be reduced to a scalar message, \(a_{i \rightarrow k}\), known as the availability. This is a measure of how strongly \(k\) believes it should an exemplar for \(i\), based on all the other datapoints \(k\) has looked at.

As usual with loopy BP, the method might oscillate, and convergence is not guaranteed. However, by using damping, the method is very reliable in practice. If the graph is densely connected, message passing takes \(O(N^2)\) time, but with sparse similarity matrices, it only takes \(O(E)\) time, where \(E\) is the number of edges or non-zero entries in \(S\).

The number of clusters can be controlled by scaling the diagonal terms \(S(i, i)\), which reflect how much each datapoint wants to be an exemplar. Figure 9.17 gives a simple example of some 2d data, where the negative Euclidean distance was used to measured similarity. The \(S(i, i)\) values were set to be the median of all the pairwise similarities. The result is 3 clusters. Many other results are reported in [FD07a], who show that the method significantly outperforms K-medoids.

# 9.4.10 Emulating BP with graph neural nets

There is a close connection between message passing in PGMs and message passing in graph neural networks (GNNs), which we discuss in Section 16.3.6. However, for PGMs, the message computations are computing using (non-learned) update equations that work for any model; all that is needed