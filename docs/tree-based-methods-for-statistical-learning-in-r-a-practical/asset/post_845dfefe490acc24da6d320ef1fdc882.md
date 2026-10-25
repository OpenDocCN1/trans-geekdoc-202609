
```
}
}
# Average VI scores across all permutations
head(vi.avg <- sort(colMeans(vi), decreasing = TRUE))
#> Overall_Qual   Gr_Liv_Area Neighborhood
#>      2959       1211        725
#> Total_Bsmt_SF First_Flr_SF     Lot_Area
#>       334        308        167
```

Note that the individual permutation importance scores are computed independently of each other, making it relatively straightforward to parallelize the whole procedure; in fact, many R implementations of Algorithm 6.1, like **vip** and **iml**, have options to do this in parallel using a number of different parallel backends.

A boxplot of the unaggregated permutation scores for the top ten features, as measured by the average across all 30 permutations, is displayed in Figure 6.1. Here, you can see that the overall quality rating of the home and its above grade square footage are two of the most important predictors of sale price, followed by neighborhood. A simple dotchart of the average permutation scores would suffice, but fails to show the variability in the individual VI scores.

![](img/2c227bfb3620dc3d159fa5e6598afa30_223_0.png)

FIGURE 6.1: Permutation-based VI scores for the top ten features in the Ames housing bagged tree ensemble, as measured by the average across all 30 permutations.

Although permutation importance is most naturally computed on the training data, it may also be useful to do the shuffling and measure performance on new data. This is discussed in depth in Molnar [2019, sec. 5.2]. Next, I’ll discuss a general technique for interpreting the effect of an individual feature (main effect) or combination of features (interaction effect).

## 6.2 Feature effects

While determining predictor importance is a crucial task in any supervised learning problem, ranking variables is only part of the story, and once a subset of “important” features is identified it is often necessary to assess the relationship between them (or subset thereof) and the response. This can be done in many ways, but in practice it is often accomplished by constructing plots of partial dependence or individual conditional expectation; see Friedman [2001] and [Goldstein et al., 2015], respectively, for details.

### 6.2.1 Partial dependence

Partial dependence (PD) plots (or PDPs) help visualize the relationship between a subset of the features (typically 1–3) and the response while accounting for the average effect of the other predictors in the model. They are particularly effective with black box models like random forests, support vector machines, and neural networks.

Let \(\boldsymbol{x} = \{x_1, x_2, \dots, x_p\}\) represent the predictors in a model whose prediction function is \(\widehat{f}(\boldsymbol{x})\). If we partition \(\boldsymbol{x}\) into an interest set, \(\boldsymbol{z}_s\), and its complement, \(\boldsymbol{z}_c = \boldsymbol{x} \setminus \boldsymbol{z}_s\), then the “partial dependence” of the response on \(\boldsymbol{z}_s\) is defined as

```
\(f_s(\boldsymbol{z}_s) = E_{\boldsymbol{z}_c} \left[ \widehat{f}(\boldsymbol{z}_s, \boldsymbol{z}_c) \right] = \int \widehat{f}(\boldsymbol{z}_s, \boldsymbol{z}_c) p_c(\boldsymbol{z}_c) d\boldsymbol{z}_c, \quad (6.1)\)
```

where \(p_c(\boldsymbol{z}_c)\) is the marginal probability density of \(\boldsymbol{z}_c\): \(p_c(\boldsymbol{z}_c) = \int p(\boldsymbol{x}) d\boldsymbol{z}_s\). Equation (6.1) can be estimated from a set of training data by

```
\(\bar{f}_s(\boldsymbol{z}_s) = \frac{1}{n} \sum_{i=1}^n \widehat{f}(\boldsymbol{z}_s, \boldsymbol{z}_{i,c}), \quad (6.2)\)
```

where \(\{\boldsymbol{z}_{i,c}\}_{i=1}^N\) are the values of \(\boldsymbol{z}_c\) that occur in the training sample; that is, we average out the effects of all the other predictors in the model.

Mathematical gibberish aside, computing partial dependence (6.2) in practice is rather straightforward. To simplify, let \(\mathbf{z}_s = x_1\) be the predictor variable of interest with unique values \(\{x_{1i}\}_{i=1}^k\). The partial dependence of the response on \(x_1\) can be constructed by following the basic steps outlined in 6.2.

### Algorithm 6.2 A simple algorithm for constructing the partial dependence of the response on a single predictor \(x_1\).

- 1) For \(i \in \{1, 2, \dots, k\}\):
  
  - (a) Copy the training data and replace the original values of \(x_1\) with the constant \(x_{1i}\).
  
  - (b) Compute the vector of predicted values from the modified copy of the training data.
  
  - (c) Compute the average prediction to obtain \(\bar{f}_1(x_{1i})\).
  
- 2) Plot the pairs \(\{x_{1i}, \bar{f}_1(x_{1i})\}_{i=1}^k\).

Algorithm 6.2 can be quite computationally intensive since it involves \(k\) passes over the training records. Fortunately, the algorithm is trivial to parallelize. It can also be easily extended to larger subsets of two or more features as well. See Greenwell [2017] for additional details and examples.

### 6.2.1.1 Classification problems

Traditionally, for classification problems, partial dependence functions are on a scale similar to the logit; see, for example, Hastie et al. [2009, pp. 369—370]. Suppose the response is categorical with \(J\) levels; then for each class we compute

```
\(f_j(x) = \log [p_j(x)] - \frac{1}{J} \sum_{j=1}^J \log [p_j(x)], \quad j = 1, 2, \dots, J, \quad (6.3)\)
```

where \(p_j(x)\) is the predicted probability for the \(j\)-th class. Plotting \(f_j(x)\) helps us understand how the log-odds for the \(j\)-th class depends on different subsets of the predictor variables. Nonetheless, there's no reason partial dependence can't be displayed on the raw probability scale. The same goes for ICE plots (Section 6.2.3). A multiclass classification example of PD plots on the probability scale is given in Section 6.2.6.

### 6.2.2 Interaction effects

While partial dependence can be used to help visualize potential interaction effects, it is often desirable to know where to look in the first place. To that end, Friedman and Popescu [2008] proposed a model-agnostic method, called the H-statistic, for identifying predictors that are involved in interactions with other variables, the strength of those interactions, as well as the identities of the other variables with which they interact.

For example, to test for the presence of an interaction effect between predictors \(x_j\) and \(x_k\), we can use the statistic

```
\( H^2_{jk} = \sum_{i=1}^N [\bar{f}_{jk}(x_{ij}, x_{ik}) - \bar{f}_j(x_{ij}) - \bar{f}_k(x_{ik})]^2 / \sum_{i=1}^N \bar{f}_{jk}(x_{ij}, x_{ik}) . \quad (6.4) \)
```

In essence, (6.4) measures the fraction of variance of \(\bar{f}_{jk}(x_j, x_k)\)—the joint partial dependence of \(y\) on \(x_j\) and \(x_k\)—not captured by \(\bar{f}_j(x_j)\) and \(\bar{f}_k(x_k)\) (the individual partial dependence of \(y\) on \(x_j\) and \(x_k\), respectively) over the training data (or representative sample thereof). Note that \(H^2_{jk} \ge 0\), with zero indicating no interaction between \(x_j\) and \(x_k\). To determine whether a single predictor, \(x_j\), say, interacts with any other variables, a similar \(H\)-statistic can be computed. Unfortunately, these statistics are not widely implemented; the R `gbm` package [Greenwell et al., 2021b], probably has the most efficient implementation (see `?gbm::interact.gbm` for details), but it's only available for GBMs (Chapter 8).

According to Friedman and Popescu [2008], only predictors with strong main effects (e.g., high relative importance) should be examined for potential interactions; the strongest interactions can then be further explored via two-way PD plots. Be warned, however, that collinearity among predictors can lead to spurious interactions that are not present in the target function.

A major drawback of the \(H\)-statistic (6.4) is that it requires computing both the individual and joint partial dependence functions, which can be expensive; the fast recursion method of Section 8.6.1 makes it feasible to compute the \(H\)-statistic for binary decision trees (and ensembles of shallow trees). A simpler approach, based on just the joint partial dependence function, is discussed in Greenwell et al. [2018].

### 6.2.3 Individual conditional expectations

PD plots can be misleading in the presence of strong interaction effects [Goldstein et al., 2015] (akin to interpreting a main effect in a linear model that's
