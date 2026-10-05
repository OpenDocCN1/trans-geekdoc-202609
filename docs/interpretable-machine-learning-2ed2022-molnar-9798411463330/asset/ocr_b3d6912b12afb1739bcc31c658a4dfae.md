# 4.4 DECISION TREE

![](bbox=[0.298, 0.143, 0.792, 0.439])

Figure 4.17: Regression tree fitted on the bike rental data. The maximum allowed depth for the tree was set to 2. The trend feature (days since 2011) and the temperature (temp) have been selected for the splits. The boxplots show the distribution of bicycle counts in the terminal node.

The data ends up in distinct groups that are often easier to understand than points on a multi-dimensional hyperplane as in linear regression. The interpretation is arguably pretty simple.

The tree structure also has a natural visualization, with its nodes and edges.

Trees create great explanations as defined in the chapter on “Human-Friendly Explanations”. The tree structure automatically invites to think about predicted values for individual instances as counterfactuals: “If a feature became greater / smaller than the split point, the prediction would be y1 instead of y2.” The tree explanations are contrastive, you can always compare the prediction of an instance with relevant “what if”-scenarios (as defined by the tree) that are simply the other leaf nodes of the tree. If the tree is short, with a depth of three requires a maximum of three features and split points to create the explanation for the prediction of an individual instance. The truthfulness of the prediction depends on the predictive performance of the tree. The explanations for short trees are very simple and general, because for each split the instance falls into one or the other leaf, and binary decisions are easy to understand.

There is no need to transform features. In linear models, it is sometimes necessary to take the logarithm of a feature. A decision tree works equally well with any monotonic transformation