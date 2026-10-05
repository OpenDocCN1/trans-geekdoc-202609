# 4.6 RuleFit

the binary decisions that lead to a certain node with “AND”, and voilà, you have a rule. It is desirable to generate a lot of diverse and meaningful rules. Gradient boosting is used to fit an ensemble of decision trees by regressing or classifying y with your original features X. Each resulting tree is converted into multiple rules. Not only boosted trees, but any ensemble algorithm can be used to generate the trees for RuleFit. A tree ensemble can be described with this general formula:

```
\tilde{f}(x) = a_0 + \sum_{m=1}^M a_m \hat{f}_m(X)
```

M is the number of trees and $\hat{f}_m(x)$ is the prediction function of the m-th tree. The a’s are the weights. Bagged ensembles, random forest, AdaBoost and MART produce tree ensembles and we use for RuleFit.

We create the rules from all trees of the ensemble. Each rule $r_m$ takes the form of:

```
$r_m(x) = \prod_{j \in T_m} I(x_j \in s_{jm})$
```

When $T_m$ is the set of features used in the m-th tree, $I$ is the indicator function that is 1 when feature $x_j$ is in the specified set of values for the j-th feature (as specified by the tree splits) and 0 otherwise. For numerical features, $s_{jm}$ is an interval in the value range of the feature. The interval looks like one of the two cases:

```
$x_{s_{jm},lower} < x_j$
```

```
$x_j < x_{s_{jm},upper}$
```

Further splits in that feature possibly lead to more complicated intervals. For categorical features the subset s contains some specific categories of the feature.

A made up for the bike rental dataset:

```
$r_{17}(x) = I(x_{temp} < 15) \cdot I(x_{weather} \in \{good, cloudy\}) \n\cdot I(10 \leq x_{windpeed} < 20)$
```

This rule returns 1 if all conditions are met, otherwise 0. RuleFit extracts all possible rules from a tree, not only from the leaf nodes. So another rule would be created is:

```
$r_{18}(x) = I(x_{temp} < 15) \cdot I(x_{weather} \in \{good, cloudy\})$
```