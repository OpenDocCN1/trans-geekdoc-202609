![](bbox=[0.26, 0.09, 0.58, 0.21])

epsilon = 1.00
minPoints = 4

Restart

# (b) Visualization of clustering

# Figure 4.26 (Cont'd) Demonstration of the DBSCAN (from [63]).

where \( p_i \) is the \( i^{th} \) data point, \( v_j \) is the centroid of the cluster \( j \), \( C \) represents the number of clusters, and \( N \) denotes the total number of data points in the dataset. Moreover, \( U_{ij} \) is the degree of membership of \( p_i \) data point in the \( j^{th} \) cluster, and under the \( 1 \le m < \infty \) constraint, \( m \) denotes the degree of fuzziness.\(^{92}\)

Also, note that the membership matrix \( U_{ij} \) is randomly assigned as:

\( U_{ij} = \frac{1}{\sum_{k=1}^c \left( \frac{\|p_i - v_j\|}{\|p_i - v_k\|} \right)^{\frac{2}{m-1}}} \)

And, the cluster centroid is calculated as:

\( v_j = \frac{\sum_{i=1}^N U_{ij}^m p_i}{\sum_{i=1}^N U_{ij}^m} \)

# 4.1.2.5.1 Visualizing this Algorithm

Figure 4.27 shows a flowchart of the FCM algorithm.

# 4.1.2.5.2 Programming This Algorithm

The Python and R code scripts for the FCM algorithm are provided below:

# Python Package

```
```python
from fcmeans import FCM
model = FCM()
```
```

# R Package:

```
```r
> install.packages("ppclust")
> library(ppclust)
> fcm(x, centers=N)
```
```

92 \( m \) infinity results in complete fuzziness.