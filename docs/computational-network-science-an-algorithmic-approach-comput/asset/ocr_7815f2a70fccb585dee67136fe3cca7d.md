![](bbox=[0.158, 0.118, 0.803, 0.342])

Fig. 6.4. Two communities of players in sporting club.

best graph partitioning method is bipartite, which divides the graph into two clusters of equal size and minimal cut size. However, it is not possible to have a partition with a smaller cut size than 3. Therefore, the best method is optimal for dividing clusters in our graph.

# 6.4.1 Spectral Clustering

Spectral “graph” clustering technique is used to determine the number of clusters in large networks. Spectral partitioning is based on Laplacian matrix ($L$) and finding eigenvalues and eigenvectors.

Adjacency matrix $A = [W_{ij}]$, where $W_{ij}$ is the edge weight between vertices $x_i$ and $x_j$. $W_{ij} = 1$ if there is a link between nodes $i$ and $j$, otherwise $W_{ij}= 0$. The Laplacian matrix $L = D - A$, where $D$ is the diagonal matrix of node degrees. We illustrate a simple example shown in Figure 6.5.

![](bbox=[0.298, 0.773, 0.655, 0.881])

Fig. 6.5. The graph $G(9, 15)$ to be analyzed for spectral partitioning.