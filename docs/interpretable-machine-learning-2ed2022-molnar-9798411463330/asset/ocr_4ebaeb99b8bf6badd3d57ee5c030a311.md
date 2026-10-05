# 7.4 Functional Decompositon

# 7.4.5 Generalized Functional ANOVA for Dependent Features

Similar to most interpretation techniques based on sampling data (such as the PDP), the functional ANOVA can produce misleading results when features are correlated. If we integrate over the uniform distribution, when reality features are dependent, we create a new dataset that deviates from the joint distribution and extrapolates to unlikely combinations of feature values.

Hooker (2007) 20 proposed the generalized functional ANOVA, a decomposition that works for dependent features. It is a generalization of the functional ANOVA we encountered earlier, which means the functional ANOVA is a special case of the generalized functional ANOVA. The components are defined as projections of onto the space of adaptive functions:

```
$\hat{f}_S(x_S) = \text{argmin}_{g_S \in L^2(\mathbb{R}^S), S \subset P} \int \left( \hat{f}(x) - \sum_{S \subset P} g_S(x_S) \right)^2 w(x)dx.$
```

Instead of orthogonality, the components satisfy a hierarchical orthogonality condition:

```
$\hat{f}_S(x_S) | S \subset U : \int \hat{f}_S(x_S)\hat{f}_U(x_U)w(x)dx = 0$
```

Hierarchical orthogonality differs from orthogonality. For two feature sets S and U, neither of which is the subset of the other (e.g. $S = \{1,2\}$ and $U = \{2,3\}$), the components $\hat{f}_S$ and $\hat{f}_U$ are not orthogonal for the decomposition to be hierarchically orthogonal. All components for all subsets of S must be orthogonal to $\hat{f}_S$. As a result, the interpretation differs in various ways: Similar to the M-Plot in the ALE chapter, generalized ANOVA components entangle (the Marginal) effects of correlated features. Whether the components entangle also depends on the choice of weight function $w(x)$. If we choose $w$ to be the uniform distribution on the unit cube, we obtain the functional ANOVA from the section above. A natural choice for $w$ is the joint probability distribution function. However, the joint distribution is usually unknown, and difficult to estimate. A trick is to start with the uniform measure on the unit cube, and cut out areas without data.

The estimation is on a grid of points in the feature space and is stated as a minimization problem that can be solved using regression techniques. However, the components cannot be computed individually, not hierarchically, but a complex system of equations is therefore complex and computationally intensive.

> $20$Hooker, Giles. "Generalized functional ANOVA diagnostics for high-dimensional functions of dependent variables." Journal of Computational and Graphical Statistics 16.3 (2007): 709-732.