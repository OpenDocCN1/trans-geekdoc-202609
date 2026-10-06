Information gain for a classification tree node is a measure of the change in entropy of the system when data is split from the parent node into the two child nodes. It is estimated as the relative difference between the entropy of the parent $H(S_j)$ and a weighted sum of the entropies of the children $(H(S^i))$:

```
$I(S_j) = H(S_j) - \sum_{i \in L,R} \frac{|S_i|}{|S_j|} H(S_i). \quad (7.2)$
```

Here, $|S_j|$ represents the number of samples reaching the parent node, and $|S|$ represents the number of samples in each child node. As the objective is to reduce entropy for each subsequent layer of the tree, *information gain* must be maximized.

*Gini impurity*, on the other hand, takes a simpler approach, estimating the probability of misclassifying an example, based solely on the class probabilities $p(y_k)$. More specifically, it is computed by multiplying the probability of labeling class $p(y_k)$, with the probability $\sum_{k \neq i} p(y_k) = 1 - p(y_k)$ of labeling a different class, summed over all classes. This can be reduced to

```
$Gini = \sum_{k}^K p(y_k)(1 - p(y_k))\n= \sum_{k}^K (p(y_k) - p(y_k)^2)\n= \sum_{k}^K p(y_k) - \sum_{k}^K p(y_k)^2\n= 1 - \sum_{y_k \in Y} p(y_k)^2. \quad \quad (7.3)$
```

This represents the impurity of a single node, the full cost of any proposed split must be estimated by combining estimates of impurity, for the left and right splits, as the weighted sum

```
$I(S_j, \theta_j) = \sum_{i \in L,R} \frac{|S_i|}{|S_j|} Gini_i. \quad \quad (7.4)$
```

For Gini