# 500

# MACHINE LEARNING

The error is noted. In the end, the errors are aggregated. This approach does not require storing additional data to indicate which tree has a given observation.

We can use the out-of-bag approach to assess the importance of every variable within the data set. In particular, when we grow a tree, we store observations have been “in-the-bag”. We calculate the error of the prediction. We then choose a feature x and shuffle the observations in the out-of-bag part of the sample. We denote the error for case with shuffled n-th feature. Comparing two errors shows how important the n-th feature is in predicting the dependent variable.

# 25.3 IMPLEMENTATION

We start our implementation by first creating the bootstrapping function which will sample our data for each tree's growth:

```
.quantQ.rf.sampleTree::[s;n]
// s -- sample dictionary with predictor and predicted variables
// n -- sample size
// 'x'y'[x[i];s;'y'i:n]?
// z,'obi'ibi((til n) except distinct i; i);
```

This function returns a dictionary of the sampled x and y for size N, but also the out-of-bag indices of the features which were not selected and the in-of-bag indices of the features that were selected.

To create a “bootstrap” tree, we now draw a bootstrap sample of size N from the training data using the function and calculate the out-of-bag error. For all features which were not sampled for tree (out-of-bag), we predict their values and measure the prediction error:

```
.quantQ.rf.bootstrapTree::[params;m;n]; .quantQ.trees.learnTree
// params -- same as the ones required by .quantQ.trees.learnTree
// m -- select m of the features in each split
// n -- sample size
// B -- size of bootstrap: create B bootstrap samples
// z,quantQ.sampleTree::['x'ypparams;n];
tree_b:quantQ.trees.learnTree::[params;'x'y;z'x'y],enlist[m!]
-- enlist;
tree_oob: raze quantQ.predictOnTree[tree_b]each flip params['x;z
'obi];
tree_oob: update pred_error: abs obs_y{first x where y][z'y]each bitmap
from
update obs_y:params['y]zoobi from tree_oob
('B xcols update B from tree_b;
'B xcols B from tree_oob;
enlist[B!]enlist z'ibi););
```