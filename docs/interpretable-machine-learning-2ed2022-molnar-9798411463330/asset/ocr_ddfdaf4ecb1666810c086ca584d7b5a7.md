Altogether, the number of rules created from an ensemble of M trees with $t_m$ terminal nodes each is:

```
$K = \sum_{m=1}^{M} 2(t_m - 1)$
```

A trick introduced by the RuleFit authors is to learn trees with random depth so that many diverse rules with different lengths are generated. Note that we discard the predicted value in each node and only keep the conditions that lead us to a node and then create a rule from it. The weighting of the decision rules is done in step 2 of RuleFit.

Another way to fix step 1: RuleFit generates a new set of features from your original features. These features are binary and can represent complex interactions of your original features. The features are chosen to maximize the prediction task. The rules are automatically generated from the covariates matrix X. You can simply see the rules as new features based on your original features.

# Step 2: Sparse linear model

You get MANY rules in step 1. Since the first step can be seen as only feature transformation, you are still not done with fitting a model. Also, you want to reduce the number of rules. In addition to the rules, your “raw” features from your original dataset will also be used in the sparse linear model. Every rule and every original feature becomes a feature in the linear model and gets a weight estimate. The original raw features are added because trees fail at representing simple relationships between y and x. Before we train a sparse linear model, we winsorize the features so that they are more robust against outliers:

```
$l_j^*(x_j) = \min(\delta_j^-, x_j), \max(\delta_j^+, x_j))$
```

$\delta_j^-$ and $\delta_j^+$ are the quantiles of the data distribution of $x_j$. A choice of $0.05$ for $\delta$ means that any value of feature $x_j$ that is in the $5\%$ lowest or $5\%$ highest values will be set at $5\%$ or $95\%$ respectively. As a rule of thumb, you can choose $\delta = 0.025$. In addition, the linear terms need to be normalized so that they have the same prior importance as typical decision rule:

```
$l_j(x_j) = 0.4 \cdot l_j^*(x_j)/std(l_j^*(x_j))$
```

The 0.4 is the average standard deviation of rules with a uniform support distribution of $s_k \sim U(0, 1)$.

We combine both types of features to generate a new feature matrix and train a sparse linear model with Lasso, with the following structure:

```
$$\tilde{f}(x) = \hat{\beta}_0 + \sum_{k=1}^{K} \hat{\alpha}_k r_k(x) + \sum_{j=1}^{p} \hat{\beta}_j l_j(x_j)$
```