XGBoost (to be discussed further in Section 8.8.1). For comparison, a default RF using 250 trees produced a test MSE of 0.261.

![](bbox=[0.17, 0.15, 0.87, 0.44])

FIGURE 8.2: Gradient boosted depth-three regression trees for the ALS data using two different learning rates: 0.02 (black curve) and 0.50 (yellow curve). Left: results from our own `lsboost()` function. Right: results from XGBoost.

# 8.3.2 Tree-specific hyperparameters

The number of terminal nodes J controls the size (i.e., complexity) of each tree in gradient tree boosting and plays the role of an important tuning parameter for capturing interaction effects. Alternatively, you can control tree size by specifying the maximum depth. In general, a tree with maximum depth d can capture interactions up to order d. Note that a tree of depth d will have at most 2^d terminal nodes and 2^d - 1 splits. A binary tree with J terminal nodes contains J - 1 splits and can capture interactions up to order J - 1. (A J - 1-th order interaction is known as a J-way interaction effect; hence, J = 1 corresponds to an additive model with no interaction effects). The documentation for scikit-learn's implementation of GBMs^h notes that controlling tree size with J seems to give comparable results to using d = J - 1 "...but is significantly faster to train at the expense of a slightly higher training error."

^h See the "Controlling the tree size" section of the scikit-learn documentation at https://scikit-learn.org/stable/modules/ensemble.