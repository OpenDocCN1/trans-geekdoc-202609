
# Computational Network Science: An Algorithmic Approach

category. The recovered camps, denoted by $R(t)$, are individuals with previous infection who have been removed due to immunization or termination (i.e., death). The removed individuals are not able to get infected again or to transmit epidemics to others.

```
$N(t) = S(t) + I(t) + R(t) \quad\ (6.3)$
```

All individuals are considered to have an equal probability of contact (i.e., infection), denoted by $\beta$. At each time $t$, each person may infect $\beta \times N$ others with equal probability. The fraction of contacts between an infected individual and a susceptible is $S(t)/N(t)$. Therefore, the new infection rate is computed by $\beta \times N[S(t)/N(t)] \times I(t) = \beta \times S(t) \times I(t)$. The population leaving the susceptible camp is equal to the number entering the infected camp. Meanwhile, a number of individuals equal to the fraction of infected individuals are leaving this class per unit time and entering the removed class (i.e., the law of mass action). Let $\gamma$ denote the rate of infection and recovery is much faster than the timescale of births and deaths overlapped in the model. Therefore, the rate of infection change is $dR(t)/dt = \beta \times S(t) \times I(t) - \gamma \times I(t)$ and the rate of recovery is $dR(t)/dt = \gamma \times I(t)$.

There have many variations to the SIS model, including SIR and models that account for births and deaths in mathematical epidemiology (Brauer et al., 2008) with models available from Vynlicky and White (2010). Another good source of discussion of these models is Jackson (2008).

Whether epidemic grown or not, a community is a group of closely related and connected entities with similar attributes; it can also be a part of a large network with groups of communities. Entities in community can interact with other communities. A good community will interact less with the entities of an outside community and more with those of the inside community. Parts of networks form groups called clusters. These clusters can be considered to be communities. Next, we outline processes for community detection.

## 6.4 COMMUNITY DETECTION

In order to motivate a community, let us consider a project team in a firm where the team is a community and the team members have interactions. There might be interfaces from one project to another. For

![](img/b8728314847e4125cdf70bea9fd5b5a5_50_0.png)

Fig. 6.3. IT organization of a factory.

example, finance and control project teams interact with material handling, sales, and distribution in a factory. Although projects are interconnected, they are clearly identifiable communities as shown in Figure 6.3.

We begin a set of global strategies and then turn to local communities. We introduce graph partitioning where we divide the graphs into parts with minimal number of links between them. The number of links between two clusters is called cut size. If we divide the network in one group, that is, the undivided cut is 0. In partitioning, it might be desirable to specify the least number of groups and the target group size, even though communities cannot be divided in an optimal way. For example, consider a sports club with 12 players. Six of them play basketball and six of them play football. We would like to divide the entire sports network into communities (i.e., clusters) based on how closely players interact with one another. All who play similar sports interact with one another closely and they are friends. There are also a few footballers who interact with basketballers. Figure 6.4 illustrates the interactions among footballers and basketballers. The

![](img/b8728314847e4125cdf70bea9fd5b5a5_51_0.png)

Fig. 6.4. Two communities of players in sporting club.

best graph partitioning method is bipartite, which divides the graph into two clusters of equal size and minimal cut size. However, it is not possible to have a partition with a smaller cut size than 3. Therefore, the best method is optimal for dividing clusters in our graph.

### 6.4.1 Spectral Clustering

Spectral “graph” clustering technique is used to determine the number of clusters in large networks. Spectral partitioning is based on Laplacian matrix ($L$) and finding eigenvalues and eigenvectors.

Adjacency matrix $A = [W_{ij}]$, where $W_{ij}$ is the edge weight between vertices $x_i$ and $x_j$. $W_{ij} = 1$ if there is a link between nodes $i$ and $j$, otherwise $W_{ij}= 0$. The Laplacian matrix $L = D - A$, where $D$ is the diagonal matrix of node degrees. We illustrate a simple example shown in Figure 6.5.

![](img/b8728314847e4125cdf70bea9fd5b5a5_51_1.png)

Fig. 6.5. The graph $G(9, 15)$ to be analyzed for spectral partitioning.

For each node, the value of $D$ is computed based on how many edges are linked to that node. For example, for node 1, there are three edges connected from nodes 2, 3, and 4. Therefore, the degree of node 1 is 3.

```
$$\tilde{L}=D-A=\begin{bmatrix} 3 & -1 & -1 & 0 & 0 & 0 & 0 \\ -1 & 2 & -1 & 0 & 0 & 0 & 0 \\ -1 & -3 & -1 & 0 & 0 & 0 & 0 \\ 0 & 0 & -1 & 4 & -1 & 0 & 0 \\ 0 & 0 & 0 & -1 & 4 & -1 & 0 \\ 0 & 0 & 0 & -1 & 4 & -1 & -1 \\ 0 & 0 & 0 & 0 & -1 & -1 & 3 \end{bmatrix}$$ (6.4)$
```

From the Laplacian matrix shown in Equation 6.4, we compute Fielder vector $(S)$ based on eigenvalues and eigenvectors. Fielder vector has both positive and negative components and their sum must be 0.

```
$S=\begin{bmatrix} 0.33 & -0.38 \\ 0.33 & -0.48 \\ 0.33 & -0.12 \\ 0.33 & -0.16 \\ 0.33 & -0.30 \\ 0.33 & -0.24 \\ 0.33 & -0.51 \end{bmatrix}$ (6.5)$
```

From the matrix $S$ shown in Equation 6.5, we identify two communities, where all the positive values form one cluster and negative values form another (Figure 6.6). In this example, clusters are $\{1, 2, 3, 4\}$ and $\{5, 6, 7, 8\}$.

![](img/b8728314847e4125cdf70bea9fd5b5a5_52_0.png)

Fig. 6.6. Two communities derived from spectral partitioning.

52 Computational Network Science: An Algorithmic Approach

- Compute the distance matrix between the data points.
- Let each data point be a cluster.
- Repeat
  a. Merge the two closest clusters.
  b. Update the distance matrix.
- Until only a single cluster remains.

### 6.4.2 Hierarchical clustering

Hierarchical clustering is the most popular and widely used method to analyze social network data. In this method, nodes are compared with another based on their similarity. Larger groups are built by joining groups of nodes based on their similarity. A criterion is introduced to compare nodes based on their relationship. There are two types of hierarchical approaches:

- Agglomerative approach: This method is also called a bottom-up approach shown in Figure 6.7. In this method, each node represents a single cluster at the beginning; eventually, nodes start merging based on their similarities and all nodes belong to the same cluster.
- Divisive approach: This method is also called a top-down approach. Initially, all nodes belong to the same cluster; eventually, each node forms its own cluster. Divisive approach is less widely used due to its complexity compared with agglomerative approach.

There is a problem with graph partitioning. We need to specify the number and size of the desired clusters. If a network is new and large, we do not have any idea about the number of clusters and how
