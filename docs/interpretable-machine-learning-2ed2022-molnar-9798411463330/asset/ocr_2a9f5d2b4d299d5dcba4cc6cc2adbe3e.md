# CHAPTER 8 LOCAL MODEL-AGNOSTIC METHODS

```
$g(x') = \phi_0 + \sum_{j=1}^{M} \phi_j$
```

You can find this formula in similar notation in the Shapley value chapter. More about the actual estimation comes later. Let us first talk about the properties of the $\phi$'s before we go into the details of their estimation.

Shapley values are the only solution that satisfies properties of Efficiency, Symmetry, Dummy and Additivity. SHAP also satisfies these, since it computes Shapley values. In the SHAP paper, you will find discrepancies between SHAP properties and Shapley properties. SHAP describes the following three desirable:

# 1) Local accuracy

```
$\hat{f}(x) = g(x') = \phi_0 + \sum_{j=1}^{M} \phi_j x'_j$
```

If you define $\phi_0 = E_X(\hat{f}(x))$ and set all $x'_j$ to 1, this is the Shapley efficiency property. Only with a different name and using the coalition vector.

```
$\hat{f}(x) = \phi_0 + \sum_{j=1}^{M} \phi_j x'_j = E_X(\hat{f}(X)) + \sum_{j=1}^{M} \phi_j$
```

# 2) Missingness

```
$x'_j = 0 \Rightarrow \phi_j = 0$
```

Missingness says that a missing feature gets an attribution of zero. Note that $x'_j$ refers to the coalitions where a value of 0 represents the absence of a feature. In coalition notation, all feature values $x'_j$ of the instance to be explained should be '1'. The presence of a 0 would mean that the feature is missing for the instance of interest. This property is not among the properties of the 'normal' Shapley values. Why do we need it for SHAP? Lundberg calls it a 'minor book-keeping property$^{43}$. A missing feature – in theory have an arbitrary Shapley value without hurting the local accuracy property, since it is multiplied with $x'_j=0$. The Missingness property enforces that missing features get a Shapley value of 0. In practice, this is only relevant for features that:

# 3) Consistency

Let $\hat{f}_x(z') = \hat{f}(h_x(z'))$ and $z'_j$ indicate that $z'_j=0$. For any two models f and f' that satisfy:

```
$\hat{f}_x(z') - \hat{f}'_x(z') \geq f_x(z') - f'_x(z')$
```

> $^{43}$https://github.com/slundberg/shap/issues/175#issuecomment-407134438