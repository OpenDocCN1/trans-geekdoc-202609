# 420

# MACHINE LEARNING

samples, the method becomes infeasible for languages which are not able to deal with a large volume of data quickly. This is where q will show it is powerful in dealing with large-memory data sets.

Assume we are equipped with a data set, which contains N independent variables, x; all of numeric type, and one dependent variable, f, also of numeric type. We defer discussion of non-numeric types until the end of this section. A typical data set will take the following form:

```
tableFunction:([ ] x1:`$f($);;x2:`$f($);;x3:`$f($);...;f:`$f($)););
```

kNN prescribes the following procedure: consider an out-of-sample observation point, which is an array of features x1; x2; ...;xn. The training sample tableFunction, we identify the subset of k entries closest to the out-of-sample point. The subset determines our expectation of the value f corresponding to the point. The expectations have to be derived from the values in the neighbourhood: this can be based on a majority vote, or we can use probability derived from the proportions within the neighbourhood.

In order to find the subset of observations close, we use a distance measure, in general as LX, i.e.

> d(x,y) = \sum_{i=1}^N |x_i - y_i|^LX

We consider the general form of a distance metric as we introduce the voting system and the value of X will play the role of a metparameter of the model. X = 2 returns the standard Euclidean distance, for X = 1 the distance metric is derived from absolute values, while for X /, the maximum of distances of individual features is chosen.

We implement the Lx-distance as a function that takes a point and training sample and returns a vector of distances of the point from each in the training sample:

```
.quant.knn.distanceLX:[point;trainingSampleX;LX]
// point -- N-dimensional array
// trainingSampleX -- matrix of training sample points
// LX -- parameter of the distance measure
:xexp;:%LX abs point-trainingSampleX;
```

We illustrate the distance measure for three values X = 1, X = 2, and X = 10. We use point (0.2;0.3;0.0;0) and a randomly generated table with three rows.

```
update dist1::quant.knn.distanceLX((0.2;0.3;0.0;0);(x1;x2;x3);1);
dist2::quant.knn.distanceLX((0.2;0.3;0.0;0);(x1;x2;x3);2);
dist10::quant.knn.distanceLX((0.2;0.3;0.0;0);(x1;x2;x3);10) from
tableFunction:([ ]x1:3.1;x2:3.1;x3:3.1;f:3?1.0)
```