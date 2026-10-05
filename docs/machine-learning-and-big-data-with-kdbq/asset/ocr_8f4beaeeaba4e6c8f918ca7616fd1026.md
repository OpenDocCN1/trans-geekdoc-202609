# 364 DATA SCIENCE

of the data set and is considered as a separate point. We illustrate the use of the size of the function getKNNProperties as follows:

```
.quantQ.of.getKNNProperties[k; select x:(x0,'x1) from dataSet;testPoint]
```

distanceTok | 0.002619135
numberTok | 12

Further, we define the reachability of the point X from the point Y as:

```
reachability_k(X,Y) = max(d(X,Y), k-distance(Y)), (17.3)
```

where the mean is that the reachability between the two points is a maximum of their true distance and the k-distance of the point Y. The meaning of this definition is that the k-distance is the minimum distance around the point Y, or the recognition scale of the neighbourhood of point Y. Any point within the k-distance is considered to be the same.

We implement the reachability distance as a function of three arguments: the point X, the index of Y within the data set, and the size of the neighborhood:

```
.quantQ.of.reachabilityDistance:[X;indexY;data;k]
// X -- point to distance, can be out of data
// indexY -- index of the point Y, it has to come from data
// data -- the data set with column x, each observation is a row of
-- features
// k -- the parameter of the kNN
// extract point x from data where i=indexY
// component 1: distance between X and Y
distanceXY: first-th distance quantQ.of.L2Distance[x;enlist Y]
// component 2: k-th distance of Y within dataset
kDistanceY:quantQ.of.getKNNProperties[k;data;Y][distanceTok];
// return the reachability distance
:max[(distanceXY,kDistanceY)];
;
```

In the table data, we assume that the features are the common column x, each observation being an array of the features for a given observation.

We illustrate the function using a test point and the first row of the dataSet:

```
.quantQ.of.reachabilityDistance[testPoint;select x:(x0,'x1) from dataSet
-- ;k]
```

0.534306

We use the reachability distance to define the local reachability density of the observation X as:

```
ρ(X) = \frac{1}{\sum_{Y \in n_k(X)} reachability_k(X,Y)} n_k(X) (17.4)
```