# Machine Learning for Social and Behavioral Research

trees in a greedy fashion, where at each level of the tree, the split that reduces impurity the most is chosen, with no consideration to splits further down the tree. After the first split (root node), the covariate size is recursively pruned until there is no longer an improvement greater than those in the model fit.

Often this tree structure fits the data well (overfit), meaning that parts of the tree structure are unlikely to generalize to alternative samples. One strategy to overcome this propensity is to prune the initial tree to a smaller size. CART is one of the most popular implementations and inspired a host of future implementations that were variants of the original methodology. One of these is the rpart package (Therneau, Atkinson, & Ripley, 2015).

# 5.4.2 Pruning

In choosing a final model, it is common to build a large tree, and then prune the tree to select a subtree, or a smaller version of the tree that minimizes the cross-validation error. This is done to prevent “missing” an additional split (see Breiman et al., 1984) Note that the largest tree will have the lowest within-sample error. However, we generally want to choose the tree structure that will generalize the best. This can be accomplished by choosing the model with the lowest average error using k-fold cross-validation (or bootstrapping).

Oftentimes when creating a tree, the tree structure can be larger than practically interpretable, that is, the size of the tree compromises the generalizability. To test this, we first create a tree without attempting to control the size of it, then proceed to prune back the leaves to create a series of submodels (subtree). In pruning, the initial tree is pruned based on the performance of a complexity measure (α) that controls the size of the tree. The cost-complexity measure is

$R(T_p) = R(T_p) + as_{\alpha}$

where $R(T_p)$ is the error, and $s_p$ is the number of leaves (terminal nodes) for tree $T_p$ (Breiman et al., 1984). When $\alpha = 0$, then we have the original tree structure. In selecting a sequence of increasing values of $\alpha$, the models incur larger and larger penalties, creating successively smaller subtrees. Although the fit of each of the subtrees will be worse on the training data in comparison to the original tree $T_0$, we would expect better fit according to cross-validation, or with assessing the fit on a test set.