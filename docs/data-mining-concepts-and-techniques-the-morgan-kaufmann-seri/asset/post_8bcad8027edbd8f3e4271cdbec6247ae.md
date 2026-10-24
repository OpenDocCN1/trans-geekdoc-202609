
In general, a measure $Q$ on clustering quality is effective if it satisfies the following four essential criteria:

- **Cluster homogeneity.** This requires that the purer the clusters in a clustering are, the better the clustering. Suppose that the ground truth says that the objects in a data set, $D = \{a, b, c, d, e, f, g, h\}$, can belong to three categories. Objects $a$ and $b$ are in category $L_1$, objects $c$ and $d$ belong to category $L_2$, and the others are in category $L_3$. Consider clustering, $\mathcal{C}_1 = \{\{a, b, c, d\}, \{e, f, g, h\}\}$, wherein a cluster $\{a, b, c, d\} \in \mathcal{C}_1$ contains objects from two categories, $L_1$ and $L_2$. Also consider clustering $\mathcal{C}_2 = \{\{a, b\}, \{c, d\}, \{e, f, g, h\}\}$, which is identical to $\mathcal{C}_1$ except that $\mathcal{C}_2$ is split into two clusters containing the objects in $L_1$ and $L_2$, respectively. A clustering quality measure, $Q$, respecting cluster homogeneity should give a higher score to $\mathcal{C}_2$ than $\mathcal{C}_1$, that is, $Q(\mathcal{C}_2, C_g) > Q(\mathcal{C}_1, C_g)$.

- **Cluster completeness.** This is the counterpart of cluster homogeneity. Cluster completeness requires that for a clustering, if any two objects belong to the same category according to the ground truth, then they should be assigned to the same cluster. Cluster completeness requires that a clustering should assign objects belonging to the same category (according to the ground truth) to the same cluster. Continue our previous example. Suppose clustering $\mathcal{C}_3 = \{\{a, b\}, \{c, d\}, \{e, f\}, \{g, h\}\}$. $\mathcal{C}_3$ and $\mathcal{C}_2$ are identical except that $\mathcal{C}_3$ split the objects in category $L_3$ into two clusters. Then, a clustering quality measure, $Q$, respecting cluster completeness should give a higher score to $\mathcal{C}_2$, that is, $Q(\mathcal{C}_2, C_g) > Q(\mathcal{C}_1, C_g)$.

- **Rag bag.** In many practical scenarios, there is often a “rag bag” category containing objects that cannot be merged with other objects. Such a category is often called “miscellaneous,” “other,” and so on. The rag bag criterion states that putting a heterogeneous object into a pure cluster should be penalized more than putting it into a rag bag. Consider a clustering $\mathcal{C}_1$ and a cluster $C \in \mathcal{C}_1$ such that all objects in $C$ except for one, denoted by $o$, belong to the same category according to the ground truth. Consider a clustering $\mathcal{C}_2$ identical to $\mathcal{C}_1$ except that $o$ is assigned to a cluster $C' \neq C$ in $\mathcal{C}_2$ such that $C'$ contains objects from various categories according to ground truth, and thus is noisy. In other words, $C'$ in $\mathcal{C}_2$ is a rag bag. Then, a clustering quality measure $Q$ respecting the rag bag criterion should give a higher score to $\mathcal{C}_2$, that is, $Q(\mathcal{C}_2, C_g) > Q(\mathcal{C}_1, C_g)$.

- **Small cluster preservation.** If a small category is split into small pieces in a clustering, those small pieces may likely become noise and thus the small category cannot be discovered from the clustering. The small cluster preservation criterion states that splitting a small category into pieces is more harmful than splitting a large category into pieces. Consider an extreme case. Let $D$ be a data set of $n + 2$ objects such that, according to ground truth, $n$ objects, denoted by $o_1, \dots, o_n$, belong to one category and the other two objects, denoted by $o_{n+1}, o_{n+2}$, belong to another category. Suppose clustering $\mathcal{C}_1$ has three clusters, $C_1^1 = \{o_1, \dots, o_n\}$, $C_2^1 = \{o_{n+1}\}$, and $C_3^1 = \{o_{n+2}\}$. Let clustering $\mathcal{C}_2$ have three clusters, too, namely $C_1^2 = \{o_1, \dots, o_{n-1}\}$, $C_2^2 = \{o_n\}$, and $C_3^2 = \{o_{n+1}, o_{n+2}\}$. In other words, $\mathcal{C}_1$ splits the small category and $\mathcal{C}_2$ splits the big category. A clustering quality measure $Q$ preserving small clusters should give a higher score to $\mathcal{C}_2$, that is, $Q(\mathcal{C}_2, C_g) > Q(\mathcal{C}_1, C_g)$.

## Categories of extrinsic methods

The ground truth may be used in different ways to evaluate clustering quality, which lead to different extrinsic methods. In general, the extrinsic methods can be categorized according to how the ground truth is used as follows.

- The matching-based methods examine how well the clustering results match the ground truth in partitioning the objects in the data set. For example, the purity methods assess how a cluster matches only those objects in one group in the ground truth.

- The information theory–based methods compare the distribution of the clustering results and that of the ground truth. Entropy or other measures in information theory are often employed to quantify the comparison. For example, we can measure the conditional entropy between the clustering results and the ground truth to measure whether there exists dependency between the information of the clustering results and the ground truth. The higher the dependency, the better the clustering results.

- The pairwise comparison–based methods treat each group in the ground truth as a class and then check the pairwise consistency of the objects in the clustering results. The clustering results are good if more pairs of objects of the same class are put into the same cluster, less pairs of objects of different classes are put into the same cluster, and less pairs of objects of the same class are put into different clusters.

Next, let us use some examples to illustrate the above categories of extrinsic methods.

### Matching-based methods

The matching-based methods compare clusters in the clustering results and the groups in the ground truth. Let us use an example to explain the ideas.

Suppose a clustering method partitions a set of objects $D = \{o_1, \dots, o_n\}$ into clusters $\mathcal{C} = \{C_1, \dots, C_m\}$. The ground truth $\mathcal{G}$ also partitions the same set of objects into groups $\mathcal{G} = \{G_1, \dots, G_l\}$. Let $C(o_x)$ and $G(o_x)$ ($1 \le x \le n$) be the cluster-id and the group-id of object $o_x$ in the clustering results and the ground truth, respectively.

For a cluster $C_i$ ($1 \le i \le m$), how well $C_i$ matches group $G_j$ in the ground truth can be measured by $|C_i \cap G_j|$, the larger the better. $\frac{|C_i \cap G_j|}{|C_i|}$ can be regarded as the purity of cluster $C_i$, where $G_j$ matching $C_i$ maximizes $|C_i \cap G_j|$. The purity of the whole clustering results can be calculated as the weighted sum of the purity of the clusters. That is,

```
purity = \sum_{i=1}^m \frac{|C_i|}{n} \max_{j=1}^l \{ \frac{|C_i \cap G_j|}{|C_i|} \} = \frac{1}{n} \sum_{i=1}^m \max_{j=1}^l \{|C_i \cap G_j|\}.
(8.29)
```

The higher the purity, the purer are the clusters, that is, the more objects in each cluster belong to the same group in the ground truth. When the purity is 1, each cluster either matches a group perfectly or is a subset of a group. In other words, no two objects belong to two groups are mixed in one cluster. However, it is possible that multiple clusters partition a group in the ground truth.

### Example 8.10. Purity.

Consider the set of objects $D = \{a, b, c, d, e, f, g, h, i, j, k\}$. The clustering ground truth and two clusterings $\mathcal{C}_1$ and $\mathcal{C}_2$ output by two methods are shown in Table 8.1.

The purity of clustering $\mathcal{C}_1$ is calculated by $\frac{1}{11} \times (4 + 2 + 4 + 1) = \frac{11}{11} = 1$ and that of clustering $\mathcal{C}_2$ is $\frac{1}{11}(2 + 3 + 1) = \frac{6}{11}$. In terms of purity, $\mathcal{C}_1$ is better than $\mathcal{C}_2$. Please note that, although $\mathcal{C}_1$ has purity 1, it splits $G_1$ in the ground truth into two clusters, $C_1$ and $C_2$.

There are some other matching based methods further refine the measurement of matching quality, such as maximum matching and using F-measure.
