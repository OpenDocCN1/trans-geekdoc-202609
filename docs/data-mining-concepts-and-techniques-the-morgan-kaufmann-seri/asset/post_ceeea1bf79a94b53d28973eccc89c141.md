

```
P(o_i|\Theta_j) = \frac{1}{\sqrt{2\pi}\sigma_j} e^{-\frac{(o_i-\mu_j)^2}{2\sigma^2}} . \quad (9.9)
```

Assuming that each cluster has the same probability, that is \(\omega_1 = \omega_2 = \cdots = \omega_k = \frac{1}{k}\), and plugging Eq. (9.9) into Eq. (9.7), we have

```
P(o_i|\Theta) = \frac{1}{k} \sum_{j=1}^k \frac{1}{\sqrt{2\pi}\sigma_j} e^{-\frac{(o_i-\mu_j)^2}{2\sigma^2}} . \quad (9.10)
```

Applying Eq. (9.8), we have

```
P(\mathbf{O}|\Theta) = \frac{1}{k} \prod_{i=1}^n \sum_{j=1}^k \frac{1}{\sqrt{2\pi}\sigma_j} e^{-\frac{(o_i-\mu_j)^2}{2\sigma^2}} . \quad (9.11)
```

The task of probabilistic model-based cluster analysis using a univariate Gaussian mixture model is to infer \(\Theta\) such that Eq. (9.11) is maximized.

## 9.1.3 Expectation-maximization algorithm

"How can we compute fuzzy clusterings and probabilistic model-based clusterings?" In this section, we introduce a principled approach. Let us start with a review of the \(k\)-means clustering problem and the \(k\)-means algorithm studied in Section 8.2.

It can easily be shown that \(k\)-means clustering is a special case of fuzzy clustering (Exercise 9.1). The \(k\)-means algorithm iterates until the clustering cannot be improved. Each iteration consists of two steps:

**The expectation step (E-step):** Given the current cluster centers, each object is assigned to the cluster with a center that is closest to the object. Here, an object is expected to belong to the closest cluster.

**The maximization step (M-step):** Given the cluster assignment, for each cluster, the algorithm adjusts the center so that the sum of the distances from the objects assigned to this cluster and the new center is minimized. That is, the similarity of objects assigned to a cluster is maximized.

We can generalize this two-step method to tackle fuzzy clustering and probabilistic model-based clustering. In general, an **expectation-maximization (EM) algorithm** is a framework that approaches maximum likelihood or maximum a posteriori estimates of parameters in statistical models. In the context of fuzzy or probabilistic model-based clustering, an EM algorithm starts with an initial set of parameters and iterates until the clustering cannot be improved, that is, until the clustering converges or the change is sufficiently small (less than a preset threshold). Each iteration also consists of two steps:

- The **expectation step** assigns objects to clusters according to the current fuzzy clustering or parameters of probabilistic clusters.
- The **maximization step** finds the new clustering or parameters that minimize the SSE in fuzzy clustering (Eq. (9.4)) or the expected likelihood in probabilistic model-based clustering.

![](img/90c930779c8f928df6ff4481fc59f9a3_469_0.png)

FIGURE 9.2
Data set for fuzzy clustering.

**Example 9.7. Fuzzy clustering using the EM algorithm.** Consider the six points in Fig. 9.2, where the coordinates of the points are also shown. Let us compute two fuzzy clusters using the EM algorithm.

We randomly select two points, say c1 = a and c2 = b, as the initial centers of the two clusters. The first iteration conducts the expectation step and the maximization step as follows.

In the E-step, for each point we calculate its membership degree in each cluster. For any point, o, we assign o to c1 with membership weight

```
\frac{1}{\frac{1}{dist(o, c_1)^2} + \frac{1}{dist(o, c_2)^2}} = \frac{dist(o, c_2)^2}{dist(o, c_1)^2 + dist(o, c_2)^2}
```

and to c2 with membership weight \frac{dist(o,c_1)^2}{dist(o,c_1)^2+dist(o,c_2)^2}, where dist(.) is the Euclidean distance. The rationale is that, if o is close to c1 and dist(o, c1) is small, the membership degree of o with respect to c1 should be high. We also normalize the membership degrees so that the sum of degrees for an object is equal to 1.

For point a, we have wa,c1 = 1 and wa,c2 = 0. That is, a exclusively belongs to c1. For point b, we have wb,c1 = 0 and wb,c2 = 1. For point c, we have wc,c1 = \frac{41}{41+41} = 0.48 and wc,c2 = \frac{45}{45+41} = 0.52. The degrees of membership of the other points are shown in the partition matrix in Table 9.3.

In the M-step, we recalculate the centroids according to the partition matrix, minimizing the SSE given in Eq. (9.4) where we assume the parameter p = 2 in this example. The new centroid should be adjusted to

```
c_j = \frac{\sum_{each point o} w_{o,c_j}^2 o}{\sum_{each point o} w_{o,c_j}^2}, \quad (9.12)
```

where j = 1, 2.

| Iteration | E-Step | M-Step |
|---|---|---|
| 1 | \(\mathbf{M}^T = \begin{bmatrix} 1 & 0 & 0.48 & 0.42 & 0.41 & 0.47 \\ 0 & 1 & 0.52 & 0.58 & 0.59 & 0.53 \end{bmatrix}\) | \(c_1 = (8.47, 5.12)\)<br>\(c_2 = (10.42, 8.99)\) |
| 2 | \(\mathbf{M}^T = \begin{bmatrix} 0.73 & 0.49 & 0.91 & 0.26 & 0.33 & 0.42 \\ 0.27 & 0.51 & 0.09 & 0.74 & 0.67 & 0.58 \end{bmatrix}\) | \(c_1 = (8.51, 6.11)\)<br>\(c_2 = (14.42, 8.69)\) |
| 3 | \(\mathbf{M}^T = \begin{bmatrix} 0.80 & 0.76 & 0.99 & 0.02 & 0.14 & 0.23 \\ 0.20 & 0.24 & 0.01 & 0.98 & 0.86 & 0.77 \end{bmatrix}\) | \(c_1 = (6.40, 6.24)\)<br>\(c_2 = (16.55, 8.64)\) |

In this example,

\(c_1 = \left( \frac{1^2 \times 3 + 0^2 \times 4 + 0.48^2 \times 9 + 0.42^2 \times 14 + 0.41^2 \times 18 + 0.47^2 \times 21}{1^2 + 0^2 + 0.48^2 + 0.42^2 + 0.41^2 + 0.47^2}, \right.\)
\(\left. \frac{1^2 \times 3 + 0^2 \times 10 + 0.48^2 \times 6 + 0.42^2 \times 8 + 0.41^2 \times 11 + 0.47^2 \times 7}{1^2 + 0^2 + 0.48^2 + 0.42^2 + 0.41^2 + 0.47^2} \right)\)
\(= (8.47, 5.12)\)

and

\(c_2 = \left( \frac{0^2 \times 3 + 1^2 \times 4 + 0.52^2 \times 9 + 0.58^2 \times 14 + 0.59^2 \times 18 + 0.53^2 \times 21}{0^2 + 1^2 + 0.52^2 + 0.58^2 + 0.59^2 + 0.53^2}, \right.\)
\(\left. \frac{0^2 \times 3 + 1^2 \times 10 + 0.52^2 \times 6 + 0.58^2 \times 8 + 0.59^2 \times 11 + 0.53^2 \times 7}{0^2 + 1^2 + 0.52^2 + 0.58^2 + 0.59^2 + 0.53^2} \right)\)
\(= (10.42, 8.99)\).

We repeat the iterations, where each iteration contains an E-step and an M-step. Table 9.3 shows the results from the first three iterations. The algorithm stops when the cluster centers converge or the change is small enough.

> "How can we apply the EM algorithm to compute probabilistic model-based clustering?" Let us use a univariate Gaussian mixture model (Example 9.6) to illustrate.

**Example 9.8. Using the EM algorithm for mixture models.** Given a set of objects, \(\mathbf{O} = \{o_1, \dots, o_n\}\), we want to mine a set of parameters, \(\mathbf{\Theta} = \{\Theta_1, \dots, \Theta_k\}\), such that \(P(\mathbf{O}|\mathbf{\Theta})\) in Eq. (9.11) is maximized, where \(\Theta_j = (\mu_j, \sigma_j)\) are the mean and standard deviation, respectively, of the \(j\)th univariate Gaussian distribution, \((1 \le j \le k)\).

We can apply the EM algorithm. We assign random values to parameters \(\mathbf{\Theta}\) as the initial values. We then iteratively conduct the E-step and the M-step as follows until the parameters converge or the change is sufficiently small.

In the **E-step**, for each object, \(o_i \in \mathbf{O} (1 \le i \le n)\), we calculate the probability that \(o_i\) belongs to each distribution, that is,

\(P(\Theta_j|o_i, \mathbf{\Theta}) = \frac{P(o_i|\Theta_j)}{\sum_{l=1}^k P(o_i|\Theta_l)}.\) (9.13)

In the **M-step**, we adjust the parameters \(\Theta\) so that the expected likelihood \(P(\mathbf{O}|\Theta)\) in Eq. (9.11) is maximized. This can be achieved by setting

```
\(\mu_j = \frac{1}{k} \sum_{i=1}^n o_i \frac{P(\Theta_j|o_i, \Theta)}{\sum_{l=1}^k P(\Theta_l|o_i, \Theta)} = \frac{1}{k} \frac{\sum_{i=1}^n o_i P(\Theta_j|o_i, \Theta)}{\sum_{i=1}^n P(\Theta_j|o_i, \Theta)}\) (9.14)
```

and

```
\(\sigma_j = \sqrt{\frac{\sum_{i=1}^n P(\Theta_j|o_i, \Theta)(o_i - \mu_j)^2}{\sum_{i=1}^n P(\Theta_j|o_i, \Theta)}}\) (9.15)
```

In many applications, probabilistic model-based clustering has been shown to be effective because it is more general than partitioning methods and fuzzy clustering methods. A distinct advantage is that appropriate statistical models can be used to capture latent clusters. The EM algorithm is commonly used to handle many learning problems in data mining and statistics due to its simplicity. Note that, in general, the EM algorithm may not converge to the optimal solution. It may instead converge to a local maximum. Many heuristics have been explored to avoid this. For example, we could run the EM process multiple times using different random initial values. Furthermore, the EM algorithm can be very costly if the number of distributions is large or the data set contains many observed data points.

## 9.2 Clustering high-dimensional data

The clustering methods we have studied so far work well when the dimensionality of a data set is not high, that is, having, say, less than 10 attributes. There are, however, important applications of high dimensionalality. “How can we conduct cluster analysis on high-dimensional data?”

In this section, we study approaches to clustering high-dimensional data. We first discuss why clustering high-dimensional data is challenging and categorize the existing methods in clustering high-dimensional data. Then we explain several representative methods, including some methods clustering in axis-parallel subspaces and those in arbitrarily oriented subspaces. Section 9.3 explores biclustering methods, which are popularly used in biological data analysis where there are many high-dimensional data sets.

### 9.2.1 Why is clustering high-dimensional data challenging?

Before we present any specific methods for clustering high-dimensional data, let us first demonstrate the needs of cluster analysis on high-dimensional data using some examples. We examine the challenges that call for new methods. We then categorize the major ideas and methods in clustering high-dimensional data.

#### Motivations of clustering analysis on high-dimensional data

In some applications, a data object may be described by many attributes. Such objects are referred to as in a high-dimensional data space.

