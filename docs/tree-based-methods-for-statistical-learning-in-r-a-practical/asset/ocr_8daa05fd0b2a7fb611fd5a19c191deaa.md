For LS loss, (8.5) becomes

```
\gamma_{jb} = \arg \min_{\gamma} \sum_{x_i \in R_{jb}} ((y_i - f_{b-1}(x_i)) - \gamma)^2
= \arg \min_{\gamma} \sum_{x_i \in R_{jb}} (r_{i,b-1} - \gamma)^2
= \frac{1}{N_{jb}} \sum_{x_i \in R_{jb}} r_{i,b-1}
```

where \( r_{i,b-1} \) and \( N_{jb} \) are the \( i \)-th residual and number of observations in the \( j \)-th terminal node for the \( b \)-th iteration, respectively. This results in the mean of the residuals in each terminal node at the \( b \)-th iteration, which is precisely what the original regression tree induced at iteration \( b \) uses for prediction (i.e., the terminal node summaries). In other words, for the special case of LS loss, the original terminal node estimates at the \( b \)-th iteration are already optimal, and so no update (i.e., line search) is needed.

For LAD loss, \( L(f) = |y - f(x)| \), and (8.5) results in the median of the current residuals in the \( j \)-th terminal node at the \( b \)-th iteration. Solving (8.5) can be difficult for general loss functions, like those often used in binary or multi-nomial classification settings, and fast approximations are often employed (see Section 8.2.0.1).

The full gradient tree boosting algorithm is presented in Algorithm 8.1. Note that this is the original gradient tree boosting algorithm proposed in Friedman [2001]. Several variations have been proposed in the literature, each with their own enhancements, and I'll discuss some of these modifications in the sections that follow.

# ## 8.2.0.1 Loss functions

Various boosting algorithms can be defined by specifying different (surrogate) loss functions \( L(y, f) \) in Algorithm 8.1. While not a tuning parameter, it is important to use an appropriate loss function for the problem at hand—LS loss, for example, is not appropriate for every regression problem. There are several common loss functions often used in GBMs and their implementations, and a handful of these are described in Table 8.1.

For regression, LS and LAD loss are common choices. LAD loss has the benefit of being robust in the presence of long-tailed error distributions and response outliers. Regardless of loss, gradient tree boosting is already robust to long-tailed distributions or outliers in the feature space due to the robustness of the individual base learners (in this case, regression trees). Recall that trees are invariant to strictly monotone transformations of the predictors (e.g., using \( x_j \), \( e^{x_j} \), or \( \log(x_j) \) for the \( j \)-th predictor all produce the same results).