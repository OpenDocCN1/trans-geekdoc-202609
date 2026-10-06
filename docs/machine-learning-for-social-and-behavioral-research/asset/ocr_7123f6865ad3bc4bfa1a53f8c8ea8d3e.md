# TABLE 12.2. The Adjacency Matrix of 10 Students from the WeChat Network

| | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 |
|---|---|---|---|---|---|---|---|---|---||
| 1 | 0 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | 0 |
| 2 | 1 | 0 | 1 | 0 | 1 | 1 | 0 | 0 | 1 | 1 |
| 3 | 1 | 1 | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 1 |
| 4 | 1 | 1 | 1 | 0 | 1 | 0 | 1 | 1 | 0 | 0 |
| 5 | 0 | 0 | 1 | 1 | 0 | 1 | 0 | 0 | 0 | 1 |
| 6 | 0 | 0 | 1 | 1 | 1 | 0 | 1 | 0 | 0 | 1 |
| 7 | 0 | 1 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 0 |
| 8 | 0 | 0 | 1 | 1 | 0 | 0 | 0 | 0 | 1 | 0 |
| 9 | 0 | 0 | 1 | 1 | 0 | 0 | 0 | 1 | 0 | 0 |
| 10 | 1 | 0 | 1 | 1 | 1 | 1 | 0 | 0 | 0 | 0 |

"target." The WeChat network is also a binary network, in which an edge either exists or not, representing a 1 or 0. Other values can be used to measure the strength of the edges. In this case, the adjacency matrix can take categorical and continuous values. Such a network is called a weighted or valued network.

The adjacency matrix can grow big quickly. For example, Facebook has more than 2.4 billion active users in 2019. To present the Facebook information, one would need a 2.4-billion by 2.4-billion adjacency matrix. However, on average, each Facebook user has around 338 Facebook friends. Therefore, the vast majority of the edges in the adjacency matrix would be 0 (about 99.99999%). A more economical way to store network data is to use the edge list matrix. In the simplest case, one only needs a K × 2 rectangular matrix to store the network data, with K being the total number of edges in the network. The first column stores the index of the starting node and the second column stores the index of the ending node of an edge. Therefore, only the pair of nodes with a relationship will be stored. For example, for the network in Table 12.2, K = 27 for a total of 27 WeChat friendships among the 10 students. Therefore, the edge list matrix is the one shown in Table 12.2. The initial adjacency matrix needs to store 10 × 10 = 100 values. However, the edge list matrix only needs to store 27 × 2 = 54 values. For the whole WeChat network, the adjacency matrix is a 165 × 165 matrix and the edge list matrix is a 1,722 × 2 matrix, a saving of about 87% storage. For a sparse network matrix such as the Facebook example, the saving on storage is even more significant.

# Node Covariates

In addition to the network data, other information is often available in a network study. The information that can be related to the nodes or the edges. The former is called node covariates, attributes, or node features, and the