model to separate or classify the collected data points linearly through a hyperplane support vector. The mapping of the data points is the main purpose of that classifier [49]. Basically, the mapping technique is performed by support vector or kernel estimation. The mapping incorporates both linear and nonlinear data information [50, 51].

In this chapter, the radial basis kernel function [52] is utilized. A radial basis kernel is a good classifier in case the data is not linearly separable.

# 11.3.3.5 Random Forest

Random Forest is an ensemble learning technique for classification that is powered by decision trees and the majority voting mechanism [53]. This method adds some additional randomness to the process of developing trees. Instead of looking for an essential feature when dividing a node, it looks for the best feature among a random group of features [54]. As a result, it lowers overfitting in decision trees and decreases variance, enhancing accuracy [55–57].

In this proposed model, the number of estimators is 1000. Such a maximum number of estimators improves the performance of the model as well as reducing the overfitting in decision trees [58].

# 11.3.3.6 Max-Voting Classifier

The Max-Voting classifier is a meta-classifier that employs majority voting to merge any classifier [59]. The class label that a large percentage of the classifiers predicted would be the final class label. The following term defines the final class label $d_j$:

```
$d_j = mode\{C_1, C_2, ..., C_n\}$
```

where $\{C_1, C_2, ..., C_n\}$ indicates the individual classifiers that participate in the voting technique [60]. The Max-Voting algorithm is shown here:

# 11.3.3.6.1 Max-Voting Algorithm

Let $c_{i,j}$ be the predicted score on a class of $j$ labels of the $i$th classifier:

```
$\sum_{i=1}^n c_{i,j} = \max_{j=1,...,m} = \sum_{i=1}^n c_{i,j}$
```