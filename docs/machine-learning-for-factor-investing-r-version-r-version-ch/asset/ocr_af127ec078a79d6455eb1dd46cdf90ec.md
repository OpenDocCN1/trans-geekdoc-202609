An intuitive prediction for $y_i$ is the following weighted average:

$$\hat{y}_i = \frac{\sum_{j \neq i} h(D(\mathbf{x}_j, \mathbf{x}_i))y_j}{\sum_{j \neq i} h(D(\mathbf{x}_j, \mathbf{x}_i))},$$

where $h$ is a decreasing function. Thus, the further $\mathbf{x}_j$ is from $\mathbf{x}_i$, the smaller the weight in the average. A typical choice for $h$ is $h(z) = e^{-az}$ for some parameter $a > 0$ that determines how penalizing the distance $D(\mathbf{x}_j, \mathbf{x}_i)$ is. Of course, the average can be taken in the set of $k$ nearest neighbors, in which case the $h$ is equal to zero beyond a particular distance threshold:

$$\hat{y}_i = \frac{\sum_{j \in \text{neighbor}} h(D(\mathbf{x}_j, \mathbf{x}_i))y_j}{\sum_{j \in \text{neighbor}} h(D(\mathbf{x}_j, \mathbf{x}_i))}.$$

A more agnostic rule is to take $h := 1$ over the set of neighbors and in this case, all neighbors have the same weight (see the old discussion by Bailey and Jain (1978) in the case of classification). For classification tasks, the procedure involves a voting rule whereby the class with the most votes wins the contest, with possible tie-breaking methods. The interested reader can have a look at the short survey in Bhatia et al. (2010).

For the choice of optimal $k$, several complicated techniques and criteria exist (see, e.g., Ghosh (2006) and Hall et al. (2008)). Heuristic values often do the job pretty well. A rule of thumb is that $k = \sqrt{I}$ ($I$ being the total number of instances) is not too far from the optimal value, unless $I$ is exceedingly large.

Below, we illustrate this concept. We pick one date (31th of December 2006) and single out one asset (with stock\_id equal to 13). We then seek to find the $k = 30$ stocks that are the closest to this asset at this particular date. We resort to the FNN package that proposes an efficient computation of Euclidean distances (and their ordering).

```
library(FNN)              # Package for Fast Nearest Neighbors detection
knn_data <- filter(data_ml, date == "2006-12-31")   # Dataset for k-NN exercise
knn_target <- filter(knn_data, stock_id == 13) %>%  # Target observation
  dplyr::select(features)
knn_sample <- filter(knn_data, stock_id != 13) %>%  # All other observations
  dplyr::select(features)
neighbors <- get.knnx(data = knn_sample, query = knn_target, k = 30)
neighbors$nn.index         # Indices of the k nearest neighbors
```

```
##        [,1]  [,2]  [,3]  [,4]  [,5]  [,6]  [,7]  [,8]  [,9] [,10] [,11] [,12] [,13] [,14] [,15]
##  [1,]  905  876  730  548 1036  501  335  117  789   54  618  130  342  360  673
##  [1,] [,16] [,17] [,18] [,19] [,20] [,21] [,22] [,23] [,24] [,25] [,26] [,27] [,28] [,29]
##  [1,]  153  265  858  830  286 1150  166  946  192  340  162  951  376  785
##  [1,] [,30]
##  [1,]    2
```

Once the neighbors and distances are known, we can compute a prediction for the return of the target stock. We use the function $h(z) = e^{-z}$ for the weighting of instances (via the distances).

```
knn_labels <- knn_data[as.vector(neighbors$nn.index), ] %>%   # y values for neighb.
  dplyr::select(RIM_Usd)
sum(knn_labels * exp(-neighbors$nn.dist) / sum(exp(-neighbors$nn.dist)))  # Pred w. k(z)=e^(-z)
```

```
## [1] 0.003042282
```