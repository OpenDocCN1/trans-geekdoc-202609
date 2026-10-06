Eigenvector centrality of a node at time $t$ is computed with Equation 2.4, where $C(t)$ is the vector of node centralities, $A$ is the adjacency matrix, and $A'$ is the result of iterated multiplications of $A$:

```
$$\bar{C}(t) = A' \bar{C}(t) \quad (2.4)$
```

As time approaches $\infty$, the dominant eigenvalue $\gamma$ will determine the centrality vector value with the value $\gamma \times \sqrt{1}$, where $\sqrt{1}$ is the eigenvector corresponding to the dominant eigenvalue $\gamma$ (Chiang, 2012).

Let us consider a $degree$-1.5 network of a node and measure the ratio of the actual number of links in that over the total number of possible links that could exist, which yields a measure called the local clustering coefficient* (Golbeck, 2013).

*Density* of a network is the ratio of the actual number of links in network over the total number of possible links that could exist. *Cohesion* is the minimum number of edges that has to be removed before the network is disconnected.

Let us consider a cluster that is a subset of nodes $s$ and each node may count the ratio $r$ as node. $r$ is the density of its neighbors in $s$ versus the total number of its neighbors. In the set $s$, the node with the minimum $r_{\min}$ yields the value *density of cluster* (used in Chapter 7).

Whereas *centrality* is a microlevel measure, *centralization* is a macrolevel measure, which varies variance in the distribution of centrality in a network. We show the most generic form of centralization in Figure 2.2.

*Leadership* ($L$) is a measure of network dimension, computed using Equation 2.5, where $d_{\max}$ is the degree of the node with the highest

+   1. Find the most central $C^*$
2. Take centrality score of $C^*$ and subtract the centrality score of each the other node, $C_i$ from $C^*$
3. Add up the differences $D = \Sigma(C^*-C_i)$
4. Divide by what sum would be under the largest possible centralization (i.e., if the network was a star). $M = \max \Sigma(C^*-C_i)$
5. Multiply this by 100 to turn it into a percentage: (i.e., centralization=$100^* \Sigma(C^*-C_i) / \max \Sigma(C^*-C_i)$).

Figure 2.2. Centralization algorithm.