Geodesic distance, denoted by $distance_{ij}$, is the number of links in the shortest path from node $i$ to node $j$. $Diameter$ of a network is the largest geodesic distance in the connected network. Reverse distance, denoted by $RD_{ij}$, is $distance_{ij} - (1 + 	ext{Diameter})$. Metrics in Equations 2.1 and 2.2 are adapted from Valente and Foreman (1998):

```
$Integration (k) = \sum_{j\neq k} \frac{RD_{jk}}{n-1} \quad (2.1)$
```

```
$Radiality (k) = \sum_{j\neq k} \frac{RD_{kj}}{n-1} \quad (2.2)$
```

*Structural centrality* measures of a node are a host of measures reflecting the structural properties of the links surrounding a focal node. For example, degree centrality of a node is the number of edges incident on the node. *Closeness centrality* of a node is the average of the shortest path lengths from the node to all other nodes in the network. It is a rather small number in *small-networks* (Watts and Strogatz, 1998). *Betweenness centrality* of a node is a measure of the node's importance (and possibly influence as discussed in Chapter 7) and is computed using the algorithm shown in Figure 2.1.

*Eigenvector centrality* measures the centrality of neighbor nodes and has been used as a measure of *influence* and *power*, which are discussed later in this book (Bonachik and Lu, 2012). Bonachik developed a beta centrality measure $C_{BC}$ with a parameter $\alpha$ for adjusting the importance of a node's degree versus a parameter $eta$ for adjusting the importance of the neighbor's centrality. This is shown in Equation 2.3.

```
$C_{BC} = \sum_{j\in N} \alpha+[\beta \times C_{BC}(j)]=\alpha \log_{n}(i)+\beta \times \sum_{j\in N} C_{BC}(j) \quad (2.3)$
```

+   1. For every pair of nodes in the network, compute all shortest paths between them.
2. Determine a fraction of shortest paths in step 1 that include the node of interest.
3. Accumulate fractions of shortest paths that include the node of interest from step 2 for betweenness value of the node.

Fig 2.1. Betweenness value computation.