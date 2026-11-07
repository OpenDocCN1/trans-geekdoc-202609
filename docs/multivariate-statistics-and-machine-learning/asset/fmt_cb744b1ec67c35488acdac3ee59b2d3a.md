
What follows are the cluster assignments, which we also plot for variables petal length by petal width ([Figure 14.5](#c14.xhtml#f14.5)). We note from the plot that clusters 0 and 2 are somewhat intermixed:

![Figure 14.5 Cluster assignments on petal length by petal width. An overlap between clusters 0 and 2 is apparent.Return to text.⏎](images/fig14.5.jpg)

*Figure 14.5* Cluster assignments on petal length by petal width. An overlap between clusters 0 and 2 is apparent.[Return to text.⏎](#c14.xhtml#re_f14.5)

```
Out[48]:
array([1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1,
     1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1,
     1, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
     0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
     0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
     0, 0, 0, 0, 0, 0, 0, 2, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 2,
    0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0], dtype=int64)
from matplotlib import pyplot as plt
plt.scatter(iris[‘petal_length’], iris[‘petal_width’], c = groups.labels_, cmap=’cool’)
plt.show()
```

### 14.10.2 Agglomerative Clustering in R

The following is a basic hierarchical clustering routine in R using Euclidean distance via the function `hclust()`. Dendrograms based on single and average linkage are easily generated ([Figure 14.6](#c14.xhtml#f14.6)).520

![Figure 14.6 Dendrograms based on single (left) and average (right) linkage.Return to text.⏎](images/fig14.6.jpg)

*Figure 14.6* Dendrograms based on single (left) and average (right) linkage.[Return to text.⏎](#c14.xhtml#re_f14.6)

```
d <- dist(iris.data, method = “euclidean”)
clust.single <- hclust(d, method = “single”)
clust.average <- hclust(d, method = “average”)
plot(clust.single)
plot(clust.average)
```

We can also produce a variety of plots in addition to the dendrograms in [Figure 14.6](#c14.xhtml#f14.6). For example, `triangle`, `unrooted`, and `fan plots` are possibilities ([Figure 14.7](#c14.xhtml#f14.7)) using the `ape` package ([Paradis & Schliep, 2019](#ref.xhtml#re_CIT000281)).

![Figure 14.7 Triangle (left), unrooted (middle), and fan plot (right) on cluster data.Return to text.⏎](images/fig14.7.jpg)

*Figure 14.7* Triangle (left), unrooted (middle), and fan plot (right) on cluster data.[Return to text.⏎](#c14.xhtml#re_f14.7)

```
> library(ape)
> dendro <- as.dendrogram(clust.single)
> plot(dendro, type = “triangle”, ylab = “Height”)
> plot(as.phylo(clust.single), type = “unrooted”, cex = 0.6, no.margin = TRUE)
> plot(as.phylo(clust.single), type = “fan”)
```

521

Of course, the plots in [Figure 14.7](#c14.xhtml#f14.7) are challenging to visualize due to the size of the data, but they are enough to get a sense of the general idea that there are two larger clusters that come out of the data. To produce a colored dendrogram, consult the package `sparcl` ([Witten & Tibshirani, 2018](#ref.xhtml#re_CIT000389)).

In helping determine the number of clusters to keep, we can produce what is called a `silhouette plot` as well as compute the `gap statistic` ([Figure 14.8](#c14.xhtml#f14.8)), where larger values of these statistics are indicative of a preferred solution:

![Figure 14.8 Silhouette plot (left) and gap statistic plot (right) suggesting the ideal number of clusters to be between approximately two (silhouette) and six (gap).Return to text.⏎](images/fig14.8.jpg)

*Figure 14.8* Silhouette plot (left) and gap statistic plot (right) suggesting the ideal number of clusters to be between approximately two (silhouette) and six (gap).[Return to text.⏎](#c14.xhtml#re_f14.8)

```
> library(factoextra)
> p1 <- fviz_nbclust(iris.data, FUN = hcut, method = “silhouette”, k.max = 10)+
+ ggtitle(“(B) Silhouette method”)
> p1
```

We can see that the ideal number of clusters is equal to 2 for the silhouette method, which more or less agrees with the dendrogram on this data. Silhouette values are computed for each data point and then averaged per cluster. A greater than not value for average silhouette values indicates that data points are essentially “matched” well for the given cluster, and hence cluster solutions with a higher than not silhouette average value are preferred.

```
> p1 <- fviz_nbclust(iris.data, FUN = hcut, method = “gap”, k.max = 10)+
+ ggtitle(“(B) Gap method”)
```

The number of clusters suggested by the `gap statistic` is equal to 6 (however, gap values are relatively strong for anything greater than three or so clusters). Gap values correspond to the difference between within-cluster dispersion relative to a reference or null distribution. For details on how the gap statistic is calculated, see Tibshirani et al. ([2001](#ref.xhtml#re_CIT000359)). For further details on the silhouette method, see [Rousseeuw (1987)](#ref.xhtml#re_CIT000312).522

## 14.11 Density-Based Clustering: `DBSCAN`

We have thus far in this chapter surveyed `k-means` and `k-representative` clustering approaches as well as hierarchical and agglomerative paradigms. These are perhaps the most traditional and common ways of clustering across the sciences.

A third general approach to clustering which is especially useful for detecting clusters of arbitrary shape goes by the name of *density-based clustering*. One such approach is the popular `DBSCAN` algorithm, which is an acronym for *density-based spatial clustering of applications with noise*. `DBSCAN` is especially efficient for large databases. The method is similar to what are referred to as `grid-based methods` ([Aggarwal, 2015](#ref.xhtml#re_CIT000005)), but uses circular regions as building blocks for the clusters. To understand `DBSCAN`, we must first understand the notions of `dense points` and `crowded regions`.

### 14.11.1 Dense Points and Crowded Regions

`DBSCAN` operates differently than `k-representative` clustering or hierarchical clustering. Instead of building up clusters by establishing random seeds and then computing distance functions, `DBSCAN` identifies points that are in so-called `crowded regions` of the feature space, that is, where many points are in some sense already “close together.” These regions are sometimes referred to as `dense regions`. Hence, we already see a key difference between this approach and that of `k-means`. In `k-means`, the algorithm did not seek out dense spaces of any kind but instead simply selected random points to begin the clustering process. In `DBSCAN` clustering, we actually seek out what appear to be clusters *first* as defined by the density of those regions. But how exactly to define density? For this we need to implement a distance function.

The density of a data point in `DBSCAN` is defined by how many points lie within a given `radius` `ε` of the point ([Aggarwal, 2015](#ref.xhtml#re_CIT000005)). All points that lie within a radius of `ε` are considered to be in the same cluster as the `core point` so long as they are equal to or less than `MinPts`, another parameter set by the user specifying the minimum number of points (or “neighbors”) required to form the so-called “dense region” within radius `ε`. Points that are within a dense region are called `core samples` or `core points`. Other points are either `border` or `noise points`. Border points are those that are contained within the radius `ε` but have insufficient points around them by the criterion `MinPts` to consider themselves a core point. That is, border points fall within the neighborhood of core points but are not significant enough to be core points themselves because they do not have `MinPts` points around them. `Noise` points are those that are neither core points nor border points.
