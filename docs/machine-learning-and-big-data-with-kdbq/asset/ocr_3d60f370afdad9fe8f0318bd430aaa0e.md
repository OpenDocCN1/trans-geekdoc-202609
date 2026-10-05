# 366
DATA SCIENCE

```
// indices of k-neighbours - contains neighbourhood[`numberTok` elements
indicesY:exec i from data where distanceToPoint<=neighbour[
  distanceToK];
return LOF
:sum(quantQ.lof.localReachabilityDensity[:data;k] each exec x from
  data);indicesY]
Xneighbour[numberTok]*quantQ.lof.localReachabilityDensity[X;
  data;k];
```

Let us calculate the LOF to the reference point (0.5,0.5):

```
quantQ.lof.LOF[testPoint;select x:(x0,'x1) from dataSet;k]
```

1.175877

The point lies in the middle of the square, in the corner of two clusters. This point is thus hard to be identified as an outlier, in particular when k = 12 neighbours are considered. Let us increase the size of the neighbourhood to k = 10:

```
quantQ.lof.LOF[testPoint;select x:(x0,'x1) from dataSet;100]
```

1.520251

The values increase as intuition suggests that the neighbourhood “sees” the vast region around itself and refers to a broader set.
Let us calculate the local outlier factor for list of points:

```
listPoints:((0.15;0.15);(0.85;0.85);(0.15;0.85);(0.85;0.15));
```

The first two points lie in one of the clusters1 and cluster2, the remaining two points lie outside of the cluster and are produced by the noise background. The list of the corresponding LOFs reads:

```
quantQ.lof.LOF[:select x:(x0,'x1) from dataSet;k] each listPoints
```

1.06019 0.9856536 1.149604 1.40695

The results clearly support our intuition, where the LOF of the first two points is higher than the LOF of those from the noise background. The result is more prominent with outlier:

```
quantQ.lof.LOF[:select x:(x0,'x1) from dataSet;100] each ((0.15;0.15);
  (0.85;0.85);(0.15;0.85);(0.85;0.15))
```

0.985998 1.022151 2.763716 3.052752

With larger neighbourhood, the difference between the points is prominent and straightforward criteria can be defined. Further, the cluster1 is denser than the other cluster, cluster2, and the LOF reaches a value below 1, suggesting the dense region.

Finally, we illustrate how to calculate the LOF for every point of the data set data:

```
quantQ.lof.LOFdata[[data;k]
// the data set with one column x, each observation is a row of
  features
// k the parameter of the kNN
```