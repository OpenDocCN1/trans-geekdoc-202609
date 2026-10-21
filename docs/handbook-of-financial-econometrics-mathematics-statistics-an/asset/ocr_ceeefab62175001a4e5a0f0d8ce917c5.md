risk analysis, all elements could be divided into two groups: net creditors (when WInDeg > WOutDeg) or net borrower (WInDeg < WOutDeg). Low values of this measure in case of banking foreign claims analysis can be explained by two factors: attractive conditions for direct foreign investments or the realization of government financial assistance programs. In both cases, the incoming flow will be significantly higher than outgoing flows.

*Betweenness centrality* shows often the vertex is placed on the shortest path between any two nodes in the network. Betweenness centrality for node i is the sum of the proportions for all pairs of actors, j and k, in which actor i is involved in a pair's geodesic(s), i.e.,

```
$C_i^b(g) = \sum_{j<k} \frac{\sigma_{jk}(n_i)}{\sigma_{jk}}, \qquad (9C.2)$
```

where $\sigma_{jk}(n_i)$ is the number of geodesics between k and j containing $i \in /\{k,j\}$, $\sigma_{jk}$ is the total number of geodesics between k and j. In our work, it will be constructed in a way that maximizes the total sum on the edges on the shortest path. In terms of loans it could be interpreted as a measure of how often the borrower is on the most popular capital transition channel (the path with the largest capital flow between any pairs of borrowers).

*The level of closeness* shows how close the node is located to other nodes or how easy we can reach other nodes in the network from a particular one. It could be defined as the inverse of farness, which in turn is the sum of distances to all other nodes in undirected graph

```
$C_i^C(g) = \frac{1}{\sum_{i\neq j} l_{ij}(g)}, \qquad (9C.3)$
```

where $l_{ij}(g)$ is the geodesic distance between i and j in g. Thus, the more central a node the lower its total distance from all other nodes. Note that taking distances from or to all other nodes is irrelevant in undirected graphs, whereas in directed graphs distances to a node are considered a more meaningful measure of centrality. In our work, it will be constructed in a way that maximizes total capital flow on the path and shows how easy it is to reach the particular node in a network from the other nodes. In terms of loans, it shows the most efficient financial intermediaries, which attract high volume of resources.

*Eigenvector centrality* is a measure of the influence of a node in a network. It assigns relative scores to all nodes in the network based on the concept that connections to high-scoring nodes contribute more to the score of the node in question than equal connections to low-scoring nodes. The value is obtained by solving the linear system $v = A'v$, where $v$ is the vector of