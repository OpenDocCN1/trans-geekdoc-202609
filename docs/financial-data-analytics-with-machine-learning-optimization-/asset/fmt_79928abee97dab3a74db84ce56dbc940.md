
Furthermore, by the quadratic nature of the mean squared error, `c_k(t)` is the unique minimum of `∑_{x∈S_k(t)} ||x - c_k||_2^2`. By the arbitrariness of `k`, this result holds for all clusters, which then yields `L_{t,2} ≤ L_{t,1}` by summing up across clusters.

Now, since `L_{t,2} ≤ L_{t,1} ≤ L_{t-1,2}` for all `t`, and `L_{t,2} ≥ 0` by definition, we can conclude by the *monotone convergence theorem* that the objective function converges. Since there are only finitely many sample points, `S` is therefore bounded, and the *Heine–Borel theorem* ensures the limiting point exists and it is a local minimizer. Furthermore, using the fact that the sample size is finite again, then so is the total number of possible clustering scenarios. Recall that by the nature of Lloyd's algorithm, each update of clusters and centroids results in an objective function not greater in value than that in the previous step, hence we can usually achieve the optimal clustering after a finite number of steps and remain there. How many steps are needed to attain the optimal clustering depends on the choice of initial seeds.

## (II) Illustrations for `K`‐means clustering

The `K`‐means clustering method is implemented in Python using the `KMeans()` function provided in the `sklearn` library, and in `R` using the built‐in function `kmeans()`. We first illustrate its use by using Fisher's Iris data in [Programme 14.1](#c14.xhtml#c14-sec-3001) via Python and [Programme 14.2](#c14.xhtml#c14-sec-3002) via `R`.

For the Iris data, both outputs from [Programme 14.1](#c14.xhtml#c14-sec-3001) via Python and [Programme 14.2](#c14.xhtml#c14-sec-3002) via `R` give 3 clusters of sizes 38, 50, and 62. Other items given in `km_iris` include:

1. `cluster_centers_` in Python and `centers` in `R`: the mean vectors for all 4 measurements of these 3 groups;

2. `labels_` in Python and `cluster` in `R`: the assigned cluster label for each datum based on the `K`‐means clustering; note that the numbering of these group labels is arbitrary, e.g., the label 1 may represent any one of these 3 groups;

3. `inertia_` in Python and `tot.withinss` in `R`: the total within‐cluster sum of squares; see more details and discussions in the next item (III) and [Appendix *14.A.1](#c14.xhtml#c14-sec-0010).

Finally, we can produce the classification table of the labels from `K`‐means clustering with the underlying “true” species in [Programme 14.3](#c14.xhtml#c14-sec-3003) via Python and [Programme 14.4](#c14.xhtml#c14-sec-3004) via `R`.

![FIGURE 14.2 Scatter plots of pairwise components of observations for each group in the Iris flower dataset.](images/c14f002.png)

**FIGURE 14.2** Scatter plots of pairwise components of observations for each group in the Iris flower dataset.

[**TABLE 14.1**](#c14.xhtml#R_c14-tbl-0001) The correspondence between the original groups and the labels assigned for the Iris dataset.

| Label assigned || Original group |

| --- | --- |

| Python || R || `setosa` || `virginica` || `versicolor` |

| 1 || 1 || 50 || 0 || 0 |

| --- | --- | --- | --- | --- |

| 2 || 2 || 0 || 48 || 14 |

| 0 || 3 || 0 || 2 || 36 |

Again, the numbering of the label is arbitrary: in Python, the labels 0, 1, and 2 correspond to the original species of `versicolor`, `setosa`, and `virginica`, respectively; whereas in `R`, the labels 1, 2, and 3 correspond to the original species of `setosa`, `virginica`, and `versicolor` groups respectively; see [Table 14.1](#c14.xhtml#c14-tbl-0001). Therefore, the actual misclassification rates in Python and `R` are only `(14 + 2) / 150 = 10.67%`.

Next, we apply the `K`‐means clustering to the 2002 HSI example, via Python in [Programme 14.5](#c14.xhtml#c14-sec-3005) and via `R` in [Programme 14.6](#c14.xhtml#c14-sec-3006).
