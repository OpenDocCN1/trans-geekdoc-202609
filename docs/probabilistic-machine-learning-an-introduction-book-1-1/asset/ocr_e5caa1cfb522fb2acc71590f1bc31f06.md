as **spectral clustering** [SM00; Lux07].

# 21.5.1 Normalized cuts

We start by creating a weighted undirected graph **W**, where each data vector is a node, and the strength of the *i – j* edge is a measure of similarity. Typically we only connected a node to its most similar neighbors, to ensure the graph is sparse, which speeds computation.

Our goal is to find *K* clusters of similar points. That is, we want to find a **graph partition** into $S_1,\dots,S_K$ disjoint sets of nodes so as to minimize some kind of cost.

Our first attempt at a cost function is to compute the weight of connections between nodes in each cluster to nodes outside each cluster:

$$\operatorname{cut}(S_1,\dots,S_K) \triangleq \frac{1}{2}\sum_{k=1}^{K} W(S_k,\bar S_k)\tag{21.28}$$

where $W(A,B) \triangleq \sum_{i\in A,j\in B} w_{ij}$ and $\bar S_k = V \setminus S_k$ is the complement of $S_k$, where $V = \{1,\dots,K\}$.

Unfortunately the optimal solution to this often just partitions off a single node from the rest, since that minimizes the weight of the cut. To prevent this, we can divide by the size of each set, to get the following objective, known as the **normalized cut**:

$$\operatorname{Ncut}(S_1,\dots,S_K) \triangleq \frac{1}{2}\sum_{k=1}^{K} \frac{\operatorname{cut}(S_k,\bar S_k)}{\operatorname{vol}(S_k)}\tag{21.29}$$

where $\operatorname{vol}(A) \triangleq \sum_{i\in A} d_i$ is the total weight of set $A$ and $d_i = \sum_{j=1}^{N} w_{ij}$ is the weighted degree of node $i$. This splits the graph into $K$ clusters such that nodes within each cluster are similar to each other, but are different to nodes in other clusters.

We can formulate the Ncut problem in terms of searching for binary vectors $\mathbf{c}_i \in \{0,1\}^N$ that minimizes the above objective, where $c_{ik}=1$ iff point $i$ belongs to cluster $k$. Unfortunately this is NP-hard [WW93]. Below we discuss a continuous relaxation of the problem based on eigenvector methods that is easier to solve.

# 21.5.2 Eigenvectors of the graph Laplacian encode the clustering

In Sec. 20.4.9.2, we discussed the graph Laplacian, which is defined as $\mathbf{L} \triangleq \mathbf{D} - \mathbf{W}$, where $\mathbf{W}$ is a symmetric weight matrix for the graph, and $\mathbf{D} = \operatorname{diag}(d_i)$ is a diagonal matrix containing the weighted degree of each node, $d_i = \sum_j w_{ij}$. To get some intuition as to why $\mathbf{L}$ might be useful for graph-based clustering, we note the following result.

**Theorem 21.5.1.** *The set of eigenvectors of $\mathbf{L}$ with eigenvalue 0 is spanned by the indicator vectors $\mathbf{1}_{S_1},\dots,\mathbf{1}_{S_K}$, where $S_k$ are the $K$ connected components of the graph.*

*Proof.* Let us start with the case $K = 1$. If $\mathbf{f}$ is an eigenvector with eigenvalue 0, then $0 = \sum_{ij} w_{ij}(f_i - f_j)^2$. If two nodes are connected, so $w_{ij} > 0$, we must have that $f_i = f_j$. Hence $\mathbf{f}$ is constant for all vertices which are connected by a path in the graph. Now suppose $K > 1$. In this case, $\mathbf{L}$ will be block diagonal. A similar argument to the above shows that we will have $K$ indicator functions, which “select out” the connected components.