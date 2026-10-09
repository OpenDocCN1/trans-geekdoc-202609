![](bbox=[0.2, 0.11, 0.45, 0.47])

DBSCAN (Density-Based Spatial Clustering of Applications with Noise) clustering algorithm, a kind of fast-clustering algorithm [17], has a fast and good affection in processing the noise [18]. The algorithm uses threshold density as the classify standard based on a fact that one clustering algorithm can be determined by any core object of the sample [19], meanwhile the number of the clusters can be determined by the tightness of the sample distribution. Through classifying connected samples into one cluster, a cluster category is obtained. The final results of all categories are obtained by dividing all closed connected samples into different categories.

Consuming the sample set $D = (x_1, x_2, \cdots, x_m)$, $\epsilon$ describes the neighborhood distance threshold of a sample, $Minpts$ describes the threshold of the number of samples in the neighborhood where the distance of a sample is $\varepsilon$, the parameter definition of DBSCAN clustering algorithm is defined as follows:

+   1. $\varepsilon$ neighborhood: For $x_i \in D$, the neighborhood whose distance from $x_i$ is not greater than $\varepsilon$ is defined as $|N_{\varepsilon}(x_i)|$:

   $$N_{\varepsilon}(x_i) = \{x_i \in D|dist(x_i, x_j) \leq \varepsilon\} \tag{1}$$
2. Core object: For $x_i \in D$, if the $N_{\varepsilon}(x_i)$ corresponding to the neighborhood contains at least $Minpts$ samples, then the core object is defined as follows:

   $$N_{\varepsilon}(x_j)) \geq Minpts \tag{2}$$
3. Directly density-reachable: If $x_i$ is located in the $\varepsilon$ neighborhood of $x_j$, and $x_j$ is the core object, then $x_i$ is said to be direct by the density of $x_j$.
4. Density-reachable: For $x_i$ and $x_j$, if there are sample sequences $p_1, p_2, \cdots, p_T$, satisfying $p_1 = x_i, p_T = x_j$, and $p_{i+1}$ is directly reached by the density of $p_i$, then $x_j$ is said to be reachable by the density of $x_i$. In other words, the density can be reached to meet the transitivity. At this time, the transmitted samples $p_1, p_2, \cdots, p_{T-1}$ in the sequence are all core objects, because only core objects can directly reach the density of other samples. Note