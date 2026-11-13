
![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_136_0.png)

Figure 4.25 Illustration of the local outlier factor (LOF) anomaly detection process [Note: dark lines represent a k = 4 (all within reachability). The light line represents a situation of out of reachability].

## 4.1.2.3 Seasonal Hybrid Extreme Studentized Deviate (S-H-ESD) Algorithm

The Seasonal Hybrid Extreme Studentized Deviate (S-H-ESD) is the third anomaly detection algorithm that I will highlight. Unlike the others, this algorithm detects anomaly in time series and has the capability to detect such anomalies at the global and local (i.e., seasonality trends) levels, as well as identify positive and negative anomalies [87]. This algorithm was developed by Twitter [57] [88].

### How does it work?

The S-H-ESD employs time series seasonal and trend decomposition to detect anomalies. S-H-ESD model is an extension of a generalized extreme studentized deviate test, where the ESD sample mean and standard deviation are used to detect anomalies in time series, while the S-H-ESD model uses the median to minimize the number of false positives [58]. The S-H-ESD algorithm also employs piecewise approximation for long time series.

### 4.1.2.3.1 Programming This Algorithm

The Python and R codes for the S-H-ESD algorithm are provided below. This algorithm can also be found within the Exploratory platform.

### Python Package

```
import sesd
model = sesd.seasonal_esd()
```

### R Package

```
> import sesd
> model = sesd.seasonal_esd()
> install.packages("devtools")
> devtools::install_github("twitter/AnomalyDetection")
> library(AnomalyDetection)
```

## 4.1.2.4 Density-based Spatial Clustering of Application with Noise (DBSCAN) Clustering Algorithm

The DBSCAN (density-based spatial clustering of application with noise) algorithm considers the region with dense data points as a cluster [59]. Density-based clustering tends to perform the best on numerical data.

### How does it work?

This algorithm separates clusters based on differences in their density [60, 61]. The clustering analysis starts with checking whether a randomly selected data point in a dataset is a core point or not. If this point turns into a core point, then this point and its neighbors [89] are added to a new cluster. If a data point is not a core point, then a check for border or noise points is carried out. The analysis terminates when all data points are clustered [62].

### 4.1.2.4.1 Visualizing this Algorithm

As you can see in Figure 4.26 [90], there are two parameters that govern the DBSCAN analysis, namely, epsilon (a distance measure) and minPoints. An arbitrary point is first picked for analysis, and if there are more than minPoints points within a distance of epsilon from that point, then a cluster is formed. The analysis continues on this cluster to expand it. This process checks all of the new points to see if they too are surrounded by more than minPoints points within a distance of epsilon. If so, the cluster grows and vice versa.

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_138_0.png)

(a) Flowchart of DBSCAN clustering algorithm

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_138_1.png)

epsilon = 1.00
minPoints = 4

Restart
GO!

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_139_0.png)

epsilon = 1.00
minPoints = 4

Restart

### (b) Visualization of clustering

### Figure 4.26 (Cont'd) Demonstration of the DBSCAN (from [63]).

## 4.1.2.5 Fuzzy C-Means (FCM) Clustering Algorithm

The Fuzzy C-Means (FCM) clustering algorithm calculates the membership of a data point by determining the degree to which it belongs to clusters [64, 65]. Given its fuzziness, the FCM calculates the probability that a point belonging to any cluster is between zero and one [91]. Unlike other algorithms, the FCM can assign a data point to more than one cluster at the same time. Thus, the FCM turns effective for data points that do not clearly fall into specific clusters [66].

### How does it work?

The FCM starts the analysis by randomly selecting cluster centroids. This algorithm randomly initializes memberships, Uij, and computes centroid vectors vj. Each membership is updated via a minimization objective function (see Equation 4.31), at which point the analysis terminates [67].

$$
J_{\text{FCM}} = \sum_{i=1}^{N} \sum_{j=1}^{C} U_{ij}^m (p_i - v_j)^2
$$ (4.31)

where \( p_i \) is the \( i^{th} \) data point, \( v_j \) is the centroid of the cluster \( j \), \( C \) represents the number of clusters, and \( N \) denotes the total number of data points in the dataset. Moreover, \( U_{ij} \) is the degree of membership of \( p_i \) data point in the \( j^{th} \) cluster, and under the \( 1 \le m < \infty \) constraint, \( m \) denotes the degree of fuzziness [92].

Also, note that the membership matrix \( U_{ij} \) is randomly assigned as:

\[
U_{ij} = \frac{1}{\sum_{k=1}^c \left( \frac{\|p_i - v_j\|}{\|p_i - v_k\|} \right)^{\frac{2}{m-1}}}
\]

And, the cluster centroid is calculated as:

\[
v_j = \frac{\sum_{i=1}^N U_{ij}^m p_i}{\sum_{i=1}^N U_{ij}^m}
\]

### 4.1.2.5.1 Visualizing this Algorithm

Figure 4.27 shows a flowchart of the FCM algorithm.

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_140_0.png)

### Figure 4.27 Flowchart of FCM clustering algorithm.

### 4.1.2.5.2 Programming This Algorithm

The Python and R code scripts for the FCM algorithm are provided below:

### Python Package

```python
from fcmeans import FCM
model = FCM()
```

### R Package

```r
> install.packages("ppclust")
> library(ppclust)
> fcm(x, centers=N)
```

[92] \( m \) infinity results in complete fuzziness.

## 4.1.2.6 Hierarchical Clustering Algorithm

The hierarchical clustering (HC) algorithm is another clustering tool that agglomerates or divides data points into groups/clusters [68]. The agglomerative approach employs bottom-up clustering, wherein each point in the dataset is initially considered a cluster, and the most similar points are then clustered together. On the other hand, the divisive approach initially groups all the observations into one cluster and then recursively splits the most appropriate clusters until one of two conditions are met, namely, reaching the identified number of clusters, or until each observation in the dataset creates its own cluster (see Figure 4.28) [93] [68]. This algorithm was proposed by Ward [69].

### How does it work?

The HC starts by forming N number of clusters by making each data point an individual cluster. The HC then determines the two closest data points in terms of the Euclidean Distance as calculated by Equation 4.34. This process combines the data points into a single cluster (which forms N-1 clusters), and this process is repeated until there is only one large cluster [70].

distance(P1, P2) = √((x2 − x1)^2 + (y2 − y1)^2) (4.34)

where P1 and P2 are the two closest data points.

### 4.1.2.6.1 Visualizing this Algorithm

Figure 4.28 shows a schematic of how the HC algorithm works in terms of its two approaches, namely, the agglomerative and divisive approaches. Note the presence of a dendrogram, which is a common means to represent a diagram of HC analysis. The same figure also shows a flowchart of the HC algorithm.

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_141_0.png)

(a) A dendrogram example for HC algorithm

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_141_1.png)

(b) Flowchart

### Figure 4.28 Flowchart of HC algorithm.

### 4.1.2.6.2 Programming This Algorithm

The Python and R codes for the HC algorithm are provided below.

### Python Package

```python
import scipy.cluster.hierarchy as sch
model = sch.dendrogram()
```

### R Package

```r
> install.packages('fastcluster')
> library(fastcluster)
> hclust (d, method="complete", members=NULL)
```
