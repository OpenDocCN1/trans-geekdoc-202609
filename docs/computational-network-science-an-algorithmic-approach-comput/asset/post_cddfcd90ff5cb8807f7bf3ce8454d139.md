
Geodesic distance, denoted by $distance_{ij}$, is the number of links in the shortest path from node $i$ to node $j$. $Diameter$ of a network is the largest geodesic distance in the connected network. Reverse distance, denoted by $RD_{ij}$, is $distance_{ij} - (1 + \text{Diameter})$. Metrics in Equations 2.1 and 2.2 are adapted from Valente and Foreman (1998):

```
$Integration (k) = \sum_{j\neq k} \frac{RD_{jk}}{n-1} \quad (2.1)$
```

```
$Radiality (k) = \sum_{j\neq k} \frac{RD_{kj}}{n-1} \quad (2.2)$
```

*Structural centrality* measures of a node are a host of measures reflecting the structural properties of the links surrounding a focal node. For example, degree centrality of a node is the number of edges incident on the node. *Closeness centrality* of a node is the average of the shortest path lengths from the node to all other nodes in the network. It is a rather small number in *small-networks* (Watts and Strogatz, 1998). *Betweenness centrality* of a node is a measure of the node's importance (and possibly influence as discussed in Chapter 7) and is computed using the algorithm shown in Figure 2.1.

*Eigenvector centrality* measures the centrality of neighbor nodes and has been used as a measure of *influence* and *power*, which are discussed later in this book (Bonachik and Lu, 2012). Bonachik developed a beta centrality measure $C_{BC}$ with a parameter $\alpha$ for adjusting the importance of a node's degree versus a parameter $\beta$ for adjusting the importance of the neighbor's centrality. This is shown in Equation 2.3.

```
$C_{BC} = \sum_{j\in N} \alpha+[\beta \times C_{BC}(j)]=\alpha \log_{n}(i)+\beta \times \sum_{j\in N} C_{BC}(j) \quad (2.3)$
```

- 1. For every pair of nodes in the network, compute all shortest paths between them.
- 2. Determine a fraction of shortest paths in step 1 that include the node of interest.
- 3. Accumulate fractions of shortest paths that include the node of interest from step 2 for betweenness value of the node.

Fig 2.1. Betweenness value computation.

Eigenvector centrality of a node at time $t$ is computed with Equation 2.4, where $C(t)$ is the vector of node centralities, $A$ is the adjacency matrix, and $A'$ is the result of iterated multiplications of $A$:

```
$$\bar{C}(t) = A' \bar{C}(t) \quad (2.4)$$
```

As time approaches $\infty$, the dominant eigenvalue $\gamma$ will determine the centrality vector value with the value $\gamma \times \sqrt{1}$, where $\sqrt{1}$ is the eigenvector corresponding to the dominant eigenvalue $\gamma$ (Chiang, 2012).

Let us consider a $degree$-1.5 network of a node and measure the ratio of the actual number of links in that over the total number of possible links that could exist, which yields a measure called the local clustering coefficient* (Golbeck, 2013).

*Density* of a network is the ratio of the actual number of links in network over the total number of possible links that could exist. *Cohesion* is the minimum number of edges that has to be removed before the network is disconnected.

Let us consider a cluster that is a subset of nodes $s$ and each node may count the ratio $r$ as node. $r$ is the density of its neighbors in $s$ versus the total number of its neighbors. In the set $s$, the node with the minimum $r_{\min}$ yields the value *density of cluster* (used in Chapter 7).

Whereas *centrality* is a microlevel measure, *centralization* is a macrolevel measure, which varies variance in the distribution of centrality in a network. We show the most generic form of centralization in Figure 2.2.

*Leadership* ($L$) is a measure of network dimension, computed using Equation 2.5, where $d_{\max}$ is the degree of the node with the highest

- 1. Find the most central $C^*$
- 2. Take centrality score of $C^*$ and subtract the centrality score of each the other node, $C_i$ from $C^*$
- 3. Add up the differences $D = \Sigma(C^*-C_i)$
- 4. Divide by what sum would be under the largest possible centralization (i.e., if the network was a star). $M = \max \Sigma(C^*-C_i)$
- 5. Multiply this by 100 to turn it into a percentage: (i.e., centralization=$100^* \Sigma(C^*-C_i) / \max \Sigma(C^*-C_i)$).

Figure 2.2. Centralization algorithm.

degree and $d_i$ is the degree of node $i$ (Freeman, 1978; Macindoe and Richards, 2011):

```
$L = \sum_{j=1} \frac{d_{max}-d_j}{(n-2)\times(n-1)} \quad (2.5)$
```

Bonding (B) measures triadic closure in a graph (Macindoe and Richards, 2011) using Equation 2.6:

```
$B = \frac{6\times number\ of\ triangles}{number\ of\ length\ between\ two\ paths} \quad (2.6)$
```

Diversity is a measure of the number of edges in a graph that are disjoint. End vertices of such edges are not adjacent (i.e., disjoint dipoles). Diversity is shown in Equation 2.7:

```
$D = \sqrt{\frac{number\ of\ disjoint\ dipoles}{((n/4)\times(n/2)-1)^2}} \quad (2.7)$
```

Burt’s structural holes measure gaps among connected components and as such are another measure of diversity (Burt, 1995).

## 2.1 CONCLUSIONS AND FUTURE WORK

Network analysis focuses on quantification (and statistical analyses) of qualities of relative nodes' locations as well as entire network properties. SNA has been a stable tool for mathematical sociology (Borgatti et al., 2013). An active direction of interest has been intelligence analysis of human networks to understand, predict, and mitigate law enforcement as well as understand surveillance and. A second direction of interest is marketing of social media. The mission is to raise awareness of these influence.

## CHAPTER 3
### Network Games

Decision making requires reasoning. Whereas decision theory is about the process of an individual's reasoning when pertinent decision attributes can be ascertained, game theory (GT) is about the process of reasoning when pertinent decision attributes include decisions of other individuals (Fudenberg, 1991). The latter is the scenario in networks where all the decisions are interdependent. GT has been long used as a branch of mathematics (Barron, 2008) to explain economic decision making (Mas-Cole et al., 1995). We will briefly introduce GT in Section 3.1 before the discussion of network-relevant applications.

### 3.1 GAME THEORY INTRODUCTION

A is a simple tuple $\langle I, S, U \rangle$. Here $I$ is a set of individuals (i.e., players or agents in GT nomenclature). Whereas $S$ is a nonempty set of actions (i.e., strategies in GT) for agent $i$, $S_i$ is a set of all agents' strategy sets, that is, $S = \Pi S_i$.

$\mu_i: S \rightarrow R$ is the utility function (i., payoff) for agent $i$. For a combination of simultaneous decisions, agent $i$ receives a nonnegative reward. For convenience, $S_{-i}$ is used to denote the strategies of agents other than agent $i$.

Matching Pennies is a famous zero-sum game of pure conflict with two actions {head, tail}, with a payoff matrix in Figure 3.1. The minimax theorem guarantees that all zero-sum matrix games are solvable, which means we can determine strategies that maximize player payoffs (Osborne and Rubinstein, 1994).

Many real-world games have action sets with infinite cardinality such as the economic competition deciding on production of quantities described in Cournot games. In the case of two firms and a single product type, $S_i = [0, \infty \]$, which is the amount of goods that that firm $i$ will produce. Payoffs are given by Equation 3.1, where

### EXERCISES

- 1. How can zero-sum game (i.e., say in YouTube) track search queries?
- 2. Describe a network that appears to be but is not scale-free.
- 3. How can beta centrality measure be used for weighted networks?
- 4. Modify density metric for weighted networks.
