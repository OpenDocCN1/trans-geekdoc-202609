> There are two other internal cluster metrics implemented by mlr: silhouette and G2 (use listMeasures("cluster") to list the available metrics). Both metrics are more computationally expensive to compute so we won't use them here, but they are additional metrics to help us decide an appropriate number of clusters.

To perform tuning, I use the tuneParams() function. As we didn't use this function during the dimension reduction part of the book, let’s refresh our memory of the arguments:

+   1. the first argument is the name of the learner
+   2. the task argument is the name of our clustering task
+   3. the resampling argument is the name of our cross-validation strategy
+   4. the par.set argument is our hyperparameter search space
+   5. the control argument is our search method
+   6. the measures argument allows us to define which performance measures we want to calculate for each iteration of the search. Here, I ask for the Davies-Bouldin index (db), Dunn index (dunn), and pseudo F statistic (G1), in that order

Just to reiterate: when we perform the tuning, for each combination of hyperparameters, the data will be split into 10 folds and the k-means algorithm will be trained on the training set of each fold. The cases in each test set will be assigned to their nearest cluster centroid, and the internal cluster metric will be calculated on these test set clusters.

> We can supply a list of as many performance metrics as we want. All of them will be calculated for each iteration of the search, but the combination of hyperparameters that optimize the value of the first metric in the list will always be returned from tuning. The mlr package also "knows" which metrics should be maximized, and which ones should be minimized for best performance.

```
install.packages("clusterSim")
listMeasures("cluster")
tunedK <- tuneParams(kMeans, task = gvhdTask,
    resampling = kFold,
    par.set = kMeansParamSpace,
    control = gridSearch,
    measures = list(db, dunn, G1))
tunedK
Tune result:
Op. pars: centers=4; algorithm=Lloyd
db.test.mean=0.8010,dunn.test.mean=0.0489,G1.test.mean=489.5331
```