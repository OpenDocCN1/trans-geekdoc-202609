
Note: Also note that you have a `Cluster representation property` where you can choose to export the first principal component for each cluster (property value `Cluster component`). With the `Cluster component` option, the first principal component is extracted from all variables in a cluster and output as the new variable `_CLUSn` (for example, `_CLUS1`, `_CLUS2`, `_CLUS3`, and so on), and the original cluster variables are rejected. The total number of generated component variables corresponds to the number of identified clusters. For more information, see “Three new Variable Clustering features in SAS Model Studio 8.3” at [https://communities.sas.com/t5/SAS-Communities-Library/Three-new-Variable-Clustering-features-in-SAS-Model-Studio-8-3/ta-p/489430](https://communities.sas.com/t5/SAS-Communities-Library/Three-new-Variable-Clustering-features-in-SAS-Model-Studio-8-3/ta-p/489430).

### 4. Observe that the default value of the regularization parameter `Rho` (`r`) is 0.8. You do not need to change its value.

![Figure 1.1 Some JMP Help Options](`Images/Image1217.png`)

Note: You use `Rho` to control the sparsity of connections among variables. Tuning the regularization parameter from low to high increases the number of disconnected components and splits larger clusters into smaller ones. Those divided clusters naturally form a hierarchical structure during this process.

### 5. Run the `Variable Clustering` node and view the results when it is complete.

Expand the `Clustered Variables` table. This table contains all the clustered variables, a list of their cluster IDs, variable labels, first principal components, and whether they were selected. Only a subset of the selected variables is shown below.

Note: For `class variables`, the `principal component` might be blank. This is valid and expected.

![Figure 1.1 Some JMP Help Options](`Images/Image1224.png`)

The first column has cluster membership against each variable. Scrolling down in the `Clustered Variables` table shows that there are nearly 13 clusters created. Each cluster has a different number of inputs. The last column has information about the input variables selected (`YES`) or not selected (`NO`) within each cluster by the node. You can verify that the original `class variables` are kept or dropped in the selection process and not the `dummy variables`.

`Graphical LASSO` based on Friedman, Hastie, and Tibshirani (2008) is performed. It estimates the `inverse covariance matrix` at a specified regularization parameter (`r=0.8` in this case). The `inverse covariance matrix` interprets the `partial correlation` between variables given other variables. Conditional dependency among variables is interpreted by estimating the `inverse covariance matrix`. The off-diagonal elements of an `inverse covariance matrix` correspond to `partial correlations`, so the zero elements imply `conditional independence` between the pair of variables. The `conditional independence` provides a better model for understanding the direct link between variables than does simple correlation analysis, which models each pair of variables without considering other variables.

### 6. Restore the view of the `Clustered Variables` table.

### 7. Expand the `Clustered Variables Network`.

![Figure 1.1 Some JMP Help Options](`Images/Image1231.jpg`)

The `Clustered Variables Network` is a spatial map that gives the orientation and relative distance of clusters and cluster members. Cluster members with a stronger link are connected by a thicker line. There are clearly 13 clusters standing out in different color shades. Many of them seem to be closer and consequently similar. Thus, you might want to try decreasing the number of clusters.

### 8. Restore the view of the `Clustered Variables Network`.

### 9. Close the results.

![Figure 1.1 Some JMP Help Options](`Images/Image1114.png`)

## Quiz

Why bin an input?

a. It can reduce the effects of an outlier.

b. It can classify missing values (into a category or bin).

c. It can generate multiple effects.

d. All of the above.

# Chapter 6: Decision Trees: Introduction

[Introduction](#Chapter_6.xhtml#_idTextAnchor113)

[Decision Tree Algorithm](#Chapter_6.xhtml#_idTextAnchor114)

[Classification Tree](#Chapter_6.xhtml#_idTextAnchor115)

[Regression Tree](#Chapter_6.xhtml#_idTextAnchor116)

[Building a Decision Tree](#Chapter_6.xhtml#_idTextAnchor117)

[How Splits Are Chosen](#Chapter_6.xhtml#_idTextAnchor118)

[How Many Questions Are Asked?](#Chapter_6.xhtml#_idTextAnchor119)

[Details: Simple Prediction Illustration](#Chapter_6.xhtml#_idTextAnchor120)

[Demo 6.1: Building a Decision Tree Model with Default Settings](#Chapter_6.xhtml#_idTextAnchor121)

[Pros and Cons of Decision Trees](#Chapter_6.xhtml#_idTextAnchor132)

[Pros](#Chapter_6.xhtml#_idTextAnchor134)

[Cons](#Chapter_6.xhtml#_idTextAnchor135)

[Quiz](#Chapter_6.xhtml#_idTextAnchor136)

## Introduction

Decision trees and ensembles of trees are supervised learning algorithms that are widely used models for classification and regression tasks. In their simplest forms, decision trees learn a hierarchy of `if/else` questions, leading to a decision. Essentially, decision trees are statistical models designed for supervised prediction problems. Supervised prediction encompasses predictive modeling, pattern recognition, discriminant analysis, multivariate function estimation, and supervised machine learning.

But decision trees are unstable models - small changes in the training data can cause large changes in the topology of the tree. However, the overall performance of the tree remains stable (Breiman et al. 1984). You can combine many trees into “forests” to create an algorithm called a `decision tree ensemble` or `random forest` to overcome the instability that a single tree exhibits with minor perturbations of the training data.

Finally, we will discuss the dynamics and parameters to consider when building and combining decision trees.

## Decision Tree Algorithm

A decision tree is so called because the predictive model can be represented by a tree-like structure. It builds up on iteratively asking questions to partition (split) the data. The questions get more specific as the tree gets deeper. The aim is to increase the predictiveness of the model as much as possible at each split, so the model keeps gaining information about the data set.

A decision tree is read from the top down starting at the `root node`. Each `internal node` represents a split based on the values of one of the inputs. The inputs can appear in any number of splits throughout the tree. Cases move down the branch that contains its input value. In a `binary tree` with interval inputs, each `internal node` is a simple inequality. A case moves left if the inequality is true and right otherwise. The `terminal nodes` of the tree are called `leaves`. The `leaves` represent the predicted target. All cases reaching a particular leaf are given the same predicted value.

Decision trees can also have `multi-way splits` where the values of the inputs are partitioned into disjoint ranges. `Multi-way splits` request more evaluations for the candidate splits, considering all inputs in all n-way splits. For example, in `4-way splits`, all possible candidates for `2-way splits`, `3-way splits`, and `4-way splits` are evaluated.

## Classification Tree

When the target is categorical, the model is a called a classification tree. The `leaves` give the predicted class as well as the probability of class membership. A classification tree can be thought of as defining several multivariate step functions.

Figure 6.1: Classification Tree

![Figure 1.1 Some JMP Help Options](`Images/Image7251.png`)

For classification trees, the most frequent response level of the training observations in a leaf is used to classify observations in that leaf.

## Regression Tree

When the target is continuous, the model is a called a regression tree. The `leaves` give the predicted value of the target. All cases that reach a particular leaf are assigned the same predicted value.
