
# Forests 499

different structure. Often, grow a tiny fraction of data changed can grow to a very different tree topology.

The technique of random forests employs trees which optimise equation 25.3. In particular, the trees grow on every bootstrapped sample are such that correlation between any other sample is reduced, the variance is not affected much. A radical version of the random forest is to grow individual trees randomly without any optimisation and bag such trees. This, however, increases the variance of individual trees too much and the entire technique does not result in significant improvement. The recommendation is whereas:

- Given the sample data consisting of $N$ observations of $M$-dimensional vector of features $X_{in}\dots,X_{Mn}$ and variable $y_n$ with $n=1,\dots,N$, we draw the bootstrapped sample – random sample with replacement – of size $N$ from the sample, denoted for simplicity as $(X,Y)$.
- Using the bootstrapped sample $(X,Y)$, grow a tree using the following procedure: For every leaf node, select $m$ out of $M$ features and select the best split of the node by optimising a $Loss$ function.
- Split the node into two nodes, which will constitute new leaves.
- Repeat until the tree with a minimum leaf node size $n_{min}$ is grown.
- Denote the tree as $T_b$.
- Get all the bootstrapped trees $T_b^*$, with $b=1,\dots,B$ and predict the outcome based on average value – for regression problems; or vote – classification problems.

Trees are grown such that the correlation between two trees is minimised. Considering in every split only a subset of variables limits the data dependence of the tree topology while it does not introduce a significant increase of individual variances. The suitable choice of m is $\sqrt{M}$ for classifications and $M/3$ for regressions.

## 25.2.1 Out-of-Bag

Throughout the book we have already seen the use of N-fold cross-validation as a method to determine out-of-sample performance of a given method. Alternatively, we have used it as a way to determine the best possible value for meta-parameters. The cost had to pay for running the cross-validation is the general need to re-estimate the model N-times, each for different folds.

The out-of-bag method provides a suitable alternative in the case of random forests. In order to calculate the error of in-sample observation, we construct the random and predict the value only from those trees where the observation has not appeared among bootstrapped samples. Thus, if we keep for every tree an indicator of the observations used in the corresponding bootstrap, we can estimate the random forest only once, and we are already equipped with cross-validation error estimates – up to vector manipulations of aggregating the proper trees.

An alternative approach to constructing the out-of-bag estimate is to calculate the errors on the fly. Namely, after we grow the tree from the bootstrapped sample, the part of the sample not used in the bootstrap is then used to test the out-of-sample error.

The error is noted. In the end, the errors are aggregated. This approach does not require storing additional data to indicate which tree has a given observation.

We can use the out-of-bag approach to assess the importance of every variable within the data set. In particular, when we grow a tree, we store observations have been “in-the-bag”. We calculate the error of the prediction. We then choose a feature x and shuffle the observations in the out-of-bag part of the sample. We denote the error for case with shuffled n-th feature. Comparing two errors shows how important the n-th feature is in predicting the dependent variable.

## 25.3 IMPLEMENTATION

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
enlist[B!]);
```

The function returns a dictionary where the first key `tree` is our tree for bootstrap sample, `oob` containing the out-of-bag predictions, and a third entry denoted by `ibi`, which contains the in-the-bag indices for each sample. The procedure is then repeated until all B trees are created:

```
quantQ.rf.randomForest:{params}
// params dictionary, ensemble: .quantQ.rf.bootstrapTree[params;m;B];
// raze flip ensemble;
```

Using the Iris data set, we can now create a random forest of 10 trees by running the following code, which samples 3 features out of 4, m=3:

```
// size = count of data sample
// sampling 3/4 features in every breakpoint
forest: params`B!(3;10)
```

Examining the result, we see that it is a dictionary with 3 keys, ensemble, the out-of-bag predictions and the "in-the-bag" indices, i.e., the trees selected for each bootstrap sample: `tree` table – the out-of-bag predictions are both themselves, tables: `ibi` key is a dictionary (type=B) of indices used for each tree.

Let us store the ensemble of trees:

```
rf: forest`tree
```

We can access the nodes of all trees:

```
show each [rrf:b]quantq.trees.leaves select from where B=b][each
exec distinct B root
```

B i path infogains xi j

```
0 1 0 1                               s#= 1 2 3!0.2805016 0.9248187 0.9248187 1 1.7
0.9248187 01100100...
0 5 4 5 4 3 2                               s#= 1 3 0!0.1044276 0.0453719 0.1460943 2 1.6
0.1460943 00100100...
0 6 4 6 3 2 0                               s#= 1 3 0!0.1044276 0.0453719 0.1460943 2 1.6
0.1460943 00000000...
0 8 7 8 7 3 2 0                               s#= 1 2 3!0.0760098 0.2916592 0.4695652 2 1.5
0.2916592 00000000...
0 10 9 10 9 7 3 2 0                               s#= 1 2 3!0.2516292 0.9182958 0.2516292 1 5.1
0.9182958 00000000...
0 11 9 11 9 7 3 2 0                               s#= 1 2 3!0.2516292 0.9182958 0.2516292 1 5.1
0.9182958 00000000...
```

* With
