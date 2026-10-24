# Table 9.2 Set of reviews and the key-words used.

| Review_ID | Keywords |
|---|---|
| $R_1$ | digital camera, lens |
| $R_2$ | digital camera |
| $R_3$ | lens |
| $R_4$ | digital camera, lens, computer |
| $R_5$ | computer, CPU |
| $R_6$ | computer, computer game |

We can group the reviews into two fuzzy clusters, $C_1$ and $C_2$. $C_1$ is for “digital camera” and “lens,” and $C_2$ is for “computer.” The partition matrix is

$$
\mathbf{M} = \begin{bmatrix} 1 & 0 \\ 1 & 0 \\ 1 & 0 \\ \frac{2}{3} & \frac{1}{3} \\ 0 & 1 \\ 0 & 1 \end{bmatrix}.
$$

Here, we use the keywords “digital camera” and “lens” as the features of cluster $C_1$ and “computer” as the feature of cluster $C_2$. For review $R_i$ and cluster $C_j$ ($1 \le i \le 6, 1 \le j \le 2$), $w_{ij}$ is defined as

$w_{ij} = \frac{|R_i \cap C_j|}{|R_i \cap (C_1 \cup C_2)|} = \frac{|R_i \cap C_j|}{|R_i \cap (\text{digital camera, lens, computer})|}.$

In this fuzzy clustering, review $R_4$ belongs to clusters $C_1$ and $C_2$ with membership degrees $\frac{2}{3}$ and $\frac{1}{3}$, respectively.

“How can we evaluate how well a fuzzy clustering describes a data set?” Consider a set of objects, $o_1, \dots, o_n$, and a fuzzy clustering $\mathcal{C}$ of $k$ clusters, $C_1, \dots, C_k$. Let $\mathbf{M} = [w_{ij}]$ ($1 \le i \le n, 1 \le j \le k$) be the partition matrix. Let $c_1, \dots, c_k$ be the *centers* of clusters $C_1, \dots, C_k$, respectively. Here, a center can be defined either as the mean or the medoid or in other ways specific to the application.

As discussed in Chapter 8, the distance or similarity between an object and the center of the cluster to which the object is assigned can be used to measure how well the object belongs to the cluster. This idea can be extended to fuzzy clustering. For any object $o_i$ and cluster $C_j$, if $w_{ij} > 0$, then $dist(o_i, c_j)$ measures how well $o_i$ is represented by $c_j$, and thus belongs to cluster $C_j$. Because an object can participate in more than one cluster, the sum of distances to the corresponding cluster centers weighted by the degrees of membership captures how well the object fits the clustering.

Formally, for an object $o_i$, the **sum of the squared error** (SSE) is given by

$\text{SSE}(o_i) = \sum_{j=1}^k w_{ij}^p dist(o_i, c_j)^2, \quad (9.2)$