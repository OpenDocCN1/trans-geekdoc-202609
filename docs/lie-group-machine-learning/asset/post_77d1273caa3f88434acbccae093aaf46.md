
## 11 Frame bundle connection learning

This chapter introduces the connection learning algorithm based on frame bundle, which is the multi-manifold data processing model. By using this algorithm, we can unearth the inner geometry connection between different manifolds and provide an effective method for big data learning.

### 11.1 Longitudinal space learning model based on frame bundle

The frame bundle has a close relationship with the tangent bundle on a manifold. We give the following definition [1].

**Definition 11.1.** $M$ is a differential manifold and its dimension equals $m$. A frame is a combinatorial structure $(l; v_1, \dots, v_m)$, and $l$ is a point on manifold $M$. $v_1, \dots, v_m$ denote $m$ tangent bundles of point $l$ on manifold $M$. A natural projection $\pi(l, v_1, \dots, v_m) = p$ is a smooth map from $P$ to $M$, and $(P, M, \pi)$ is a frame on $M$.

The manifold learning method based on the tangent bundle usually constructs a single frame for data processing. If a small amount of noise points exist, the method should be useful. If the noise changes into another type of manifold structure and abounds, the original algorithm might lose its efficacy. $\{e_i, i = 1, 2, \dots, k\}$ is a set that includes $k$ clusters. $e_i$ represents the $i$-th cluster, which has a single manifold data structure. Therefore, the set includes a multi-manifold structure. Some studies have investigated this type of manifold structure [2]. Although these methods improve the learning process to some extent, they have some shortcomings. To overcome these shortcomings, we have to identify the relationships between different manifolds, which requires the construction of a coordinate frame. By studying the structure of a manifold, we can solve the problem easily by using a connection operator. We construct a coordinate frame for each manifold and combine them to form the coordinate coverage. We then obtain the frame bundle. Through the above analysis, we can obtain the coordinate coverage of a multi-manifold structure (Figure 11.1).

![](img/456a7a56403cbb2b5f1a261793529a51_364_0.png)

**Fig. 11.1:** Multi-manifold coordinate system.

Figure 11.1 shows a multi-manifold data set $\{M_1, M_2, M_3, \dots \}$. By using the frame projection, we can obtain a coordinate coverage $\{U, W, V, \dots \}$, and its elements consist of $m$ linearly independent vectors. We then obtain a tangent space, which is the longitudinal space in the frame bundle.

We represent each coordinate domain on a manifold by using natural coordinates $(\partial/\partial u_1, \dots, \partial/\partial u_m)$. Therefore, any frame on the manifold can be represented as

$$X_i^k\left(\frac{\partial}{\partial u^k}\right)_p, 1 \leq i \leq m.$$

Where $(X_i^k)$ is a $m*m$ non-degenerate matrix.

If noise exists in a manifold data set, the data might lose its local geometric characteristic. Therefore, the algorithm will not converge, and its accuracy rate will decrease. In the real world, noise always exists. The algorithm’s sensitivity to noise hinders its widespread use.

The theoretical basis of manifold learning includes the following:

1. When two sample points are sufficiently close, their neighbouring regions do not change after dimension reduction. This hypothesis is called local homeomorphism.
2. The sample points are required to cover the manifold. This hypothesis is called the density assumption.
3. In general, we assume that the data set is smooth and continuous. This hypothesis is called the continuity hypothesis. The noise might violate the three assumptions and yield inaccurate results.

We build a data set and show the noise problem experimentally. There are two data sets $N_1(\varphi_1, E), N_2(\varphi_2, E)$, and we have $\varphi_1 = 1, 1/\sqrt{3}, \dots, 1/\sqrt{2n+1}, \dots, 1/\sqrt{19}$, $\varphi_2 = -\varphi_1$. We employ the standard normal distribution to verify the effect of noise. The $\varphi_1$ of noise is equal to 0.1, 0.2, 0.5, and 1 respectively. The four cases were added to two data sets $N_1$, $N_2$. For each data set, we sampled 1000 points and employed the GTM algorithm [2]. The experimental results are presented below.

In Figure 11.2, four different types of noisy data are added to the 1000 sample points of $N_1$. We can see that the GTM algorithm is highly robust with a relatively small error. However, as the deviation increases, the results fluctuate severely. Figure 11.3 shows the same phenomenon, which illustrates that the noise would affect manifold learning to some extent.

Next, we will analyse the influence of noise on the manifold learning algorithm in theory. In general, we mainly analyse the local linear mapping algorithm. We assume that there is a data set $X = \{x_1, x_2, \dots, x_N\}$ in the high-dimensional space $R^d$. For any point $x_0$, $U(x_0)$ represents the neighbour domain of $x_0$. If we have $x_1, x_2, \dots, x_k \in U(x_0)$, the weight values between point $x_0$ and its neighbour points can be represented by $w_i$, and we have

$$x_0 = \sum_{i=1}^{k} w^i x_i, \quad \sum_{i=1}^{k} w^i = 1. \quad (11.2)$$

![](img/456a7a56403cbb2b5f1a261793529a51_366_0.png)

![](img/456a7a56403cbb2b5f1a261793529a51_366_1.png)

Where $x_i' = x_i + \varepsilon_i, (i = 0, 1, 2, \dots, k)$ are the neighbour points disturbed by the noise, and the corresponding transformation is as follows:

$$x_0' = \sum_{i=1}^{k} w^{i'} x_i', \quad \sum_{i=1}^{k} w^{i'} = 1. \quad (11.3)$$

Here, we have $X^0 = (x_1, x_2, \dots, x_k)$, $X^{0'} = (x_1', x_2', \dots, x_k')$, $w = (w^1, w^2, \dots, w^k)^T$, $w' = (w^{1'}, w^{2'}, \dots, w^{k'})^T$, and

$$x_0 = X^0 w, \quad x_0' = X^{0'} w'. \quad (11.4)$$

In the above case, if each noise point is independent of the other with the same mean value, we have the following definition.

**Definition 11.2.** $M$ is a smooth manifold, $X$ is the sampling point set on the manifold, and $\varepsilon$ represents the neighbour domain of $x_0$. Furthermore, $\sigma$ is the additional value of noise, and $\varepsilon^i$ represents the $i$-th component of $\varepsilon$. $l = \text{rank}(X^0)$, $\lambda_{\text{min}}$ is the minimum nonzero eigenvalue of $\varepsilon^2\varepsilon$, and $w$ is the corresponding weight value. Suppose that $\delta w = w' - w$, then we have the following function:

$$E\|\delta w\|^2 \leq \frac{k(k + 3)}{2\lambda_{\text{min}} l} E\|w'\|^2. \quad (11.5)$$

Through the above theoretical analysis, we know that noise consists of two types; one includes the weak spots of the original sample points and the other one does not belong to the former type completely. For the first case, there are many improved methods. Many algorithms consider the first case because they cannot ignore this situation. If we add a regularisation item, we can make the local linear embedding algorithm more robust [3]. The local tangent space alignment algorithm has good anti-noise capacity [4]. The local smoothing algorithm can be regarded as the pre-processing method by using the locally weighted algorithm [5]. These improved methods all focus on the first case. However, this article adopts a new method to eliminate the effect of the second type of noise for maintaining the original advantage. This section regards such noise as a new type of manifold data structure. We separate the noise from the original sample data and handle it. Therefore, we introduce the connection learning algorithm based on frame bundle.

### 11.2 Longitudinal space connection learning model based on frame bundle

In general, there is no global frame field on manifold $M$ with dimension $m$. Nevertheless, the affine connection exists. Therefore, there is a global frame field in the frame bundle $P$. We can handle multiple manifold structures from this perspective, which is easier than handling the manifold $M$.
