To derive the Chow-Liu algorithm, we can use the tree decomposition in equation 9.13 to write down the likelihood.

$$\log P(D\mid\theta,T)=\sum_t\sum_k N_{tk}\log p(x_t=k\mid\theta)+\sum_{s,t}\sum_{j,k}N_{stjk}\log\frac{p(x_s=j,x_t=k\mid\theta)}{p(x_s=j\mid\theta)p(x_t=k\mid\theta)} \tag{9.14}$$

Here, $N_{stjk}$ is the number of times node $s$ is in state $j$ and node $t$ is in state $k$ and $N_{tk}$ is the number of times node $t$ is in state $k$. We can rewrite $N_{tk}$ as $N\times p(x_t=k)$ and, similarly, $N_{stjk}$ as $N\times p(x_s=j,x_t=k)$. If we plug this in to our expression for log likelihood, we get the following.

$$\frac{1}{N}\log P(D\mid\theta,T)=\sum_{t\in V}\sum_k\hat p(x_t=k)\log\hat p(x_t=k)+\sum_{(s,t)\in E}I(x_s,x_t\mid\hat\theta_{st}) \tag{9.15}$$

Here, $I(x_s,x_t\mid\theta)$ is the mutual information between $x_s$ and $x_t$. Therefore, the tree topology that maximizes the log likelihood can be computed via the maximum weight spanning tree, where the edge weights are pairwise mutual information $I(x_s,x_t\mid\theta)$. The algorithm in equation 9.15 is known as the Chow-Liu algorithm. Note that to compute the maximum spanning tree, we can use either Prim’s algorithm or Kruskal’s algorithms, which can be implemented in $O(E\log V)$ time. In the following section, we will examine how to infer the structure of a general graph based on inverse covariance estimation.

# 9.3.2  *Inverse covariance estimation*

Identifying stock clusters helps one discover similar companies, which can be useful for comparative analysis or a pairs trading strategy. We can find similar clusters by estimating the inverse covariance (precision) matrix that can be used to construct a graph network of dependencies, using the fact that zeros in the precision matrix correspond to the absence of edges in the constructed graph. Let’s represent our unknown graph structure as a Gaussian graphical model. Let $\Lambda=\Sigma^{-1}$ represent the precision matrix of the multivariate normal. Then, the log likelihood of $\Lambda$ can be derived as follows.

$$l(\Lambda)=\log\det\Lambda-\operatorname{tr}[S\Lambda] \tag{9.16}$$