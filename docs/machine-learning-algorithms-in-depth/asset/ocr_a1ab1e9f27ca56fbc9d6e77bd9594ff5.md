# ## 8.1 Dirichlet process *K*-means

Dirichlet process (DP) *K*-means is a Bayesian nonparametric extension of the *K*-Means algorithm. *K*-means is a clustering algorithm that can be applied, for instance, to customer segmentation, where customers are grouped by purchase history, interests, and geographical location. DP-means is similar to *K*-means except that new clusters are created whenever a data point is sufficiently far away from all existing cluster centroids; therefore, the number of clusters grows with the data. DP-means converges to a local optimum of a *K*-means-like objective that includes a penalty for the number of clusters.

We select the cluster *K* based on the smallest value of the following equation.

$$\underset{k}{\arg\min}\{\|x_i-\mu_1\|^2,\ldots,\|x_i-\mu_k\|^2,\lambda\} \tag{8.1}$$

The resulting update is analogous to the *K*-means reassignment step, during which we reassign a point to the cluster corresponding to the closest mean or start a new cluster if the squared Euclidean distance is greater than $\lambda$. The DP means algorithm is summarized in figure 8.1.

```
1: Init. $K = 1$, $l_1 = \{x_1,\ldots,x_n\}$ and $\mu_1$ the global mean
2: Init. labels $z_i = 1$ for all $i = 1,\ldots,n$
3: Init. $\lambda = \text{kpp\_init}(X, K_{\text{init}})$
4: Repeat until convergence:
5: &nbsp;&nbsp;&nbsp;&nbsp;for each $x_i$:
6: &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;compute $d_{ic} = \|x_i - \mu_c\|^2$ for $c = 1,\ldots,K$
7: &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;if $\min_c d_{ic} > \lambda$, set $K = K + 1$ and $\mu_k = x_i$
8: &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;otherwise, set $z_i = \arg\min_c d_{ic}$
9: &nbsp;&nbsp;&nbsp;&nbsp;for each cluster $l_j = \{x_i|z_i = j\}$, compute $\mu_j = \frac{1}{|l_j|}\sum_{x\in l_j}x$
10: &nbsp;&nbsp;&nbsp;&nbsp;Compute the objective: $\sum_{c=1}^{K}\sum_{x\in l_c}\|x-\mu_c\|^2 + \lambda K$
```

Figure 8.1  
DP-means algorithm  
pseudo-code

To evaluate cluster performance, we can use the following metrics: normalized mutual information (NMI), variation of information (VI), and adjusted Rand index (ARI). The NMI is defined as follows.

$$\operatorname{NMI}(X,Y)=\frac{I(X;Y)}{\frac{H(X)+H(Y)}{2}} \tag{8.2}$$

Here, $H(X)$ is the entropy of $X$ and $I(X;Y)$ is the mutual information between the ground truth label assignments $X$ (when they are available) and the computed assignments $Y$. For a review of information measures, see *Elements of Information Theory* by Thomas M. Cover and Joy A. Thomas (Wiley, 2006) for details.