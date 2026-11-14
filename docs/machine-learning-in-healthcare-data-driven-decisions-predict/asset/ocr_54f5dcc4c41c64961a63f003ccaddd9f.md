# 4.2 Betweenness Centrality

This matrix is dependent upon the shortest path.

It is the overall length of path, which is shortest and passing though the vertex or node, and it is determined by the Betweenness Centrality of that node.

Let's say the starting node is i and the ending node is j. The calculation for the Betweenness Centrality for node k is,
BC_k = \sum_{each shortest path} shortest path having node k

There can be more number of paths that are shorter between vertices or nodes i and j, these things also affect the measurement of the Betweenness Centrality.
BC_k = \sum_{each shortest path} (shortest path having node k/total number of paths that are shorter between i and j).

# 4.3 Clustering Coefficient

The clustering coefficient estimates the extent to which individual elements (vertices) in a network exhibit clustering propensity. It offers information on the local connectivity or cohesion of neighborhoods inside the network. Various methods exist for computing the clustering coefficient, but a prevalent one involves examining a node and its adjacent nodes. The clustering coefficient of an individual element (vertex) is the quotient of the number of closed triplets centered at that node to the total number of potential triangles. High clustering signifies the existence of closely related clusters.

The global clustering coefficient is computed by taking the average of the clustering coefficients for each node in the network. It provides a comprehensive assessment of the level of clustering in the whole network.

Clustering coefficient of an individual element (node/vertex) i can be given as;

CC_i = \frac{2 \times number of triangles centered at node i}{degree of node i \times (degree of node i - 1)}

The global clustering coefficient is estimated by taking the average of the local clustering coefficients CC_i for all nodes in a network.

# 4.4 Closeness Centrality

The idea of proximity to other nodes in the network is represented by this metric. In comparison to fewer central nodes, more central nodes have shorter distances or better closeness centrality scores, which allow them to converse more quickly and easily with others. In contrast, nodes with lower proximity centrality scores are farther away from one another and require longer paths to connect to other vertices in the network.