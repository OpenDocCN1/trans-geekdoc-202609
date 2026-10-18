
Specifically, let `n_tail` denote the number of data points greater than `x̂_min` in the observed dataset of size `n`, whose truncated distance is denoted by `K*(x̂_min)`. We generate a total of `M` (usually ranging from 1,000 to 10,000) bootstrapped samples, each of size `n`, where every sample point is generated independently in the following manner: with a probability of `n_tail / n`, the point is generated from the power law distribution with the scaling parameter `β̂` and the support `x ≥ x̂_min`; otherwise, with a probability of `1 - n_tail / n`, the point is drawn uniformly from the portion below `x̂_min` in the original observed dataset. We then calculate the truncated KS distance for the `m`-th bootstrapped sample, denoted by `K_m(x̂_min)`, for `m = 1, ..., M`, and the `p`-value of this test is defined as the empirical survival function of the bootstrapped truncated KS distances at `K*(x̂_min)`:

```
p-value := |{m : K_m(x̂_min) > K*(x̂_min)}| / M.
```

Intuitively, a small `p`-value below a pre-specified significance level `α` indicates that the truncated KS distance of the observed dataset is larger than most of those in the bootstrapped samples, leading to the rejection of the null hypothesis at the significance level `α` that the upper tail of the dataset follows the fitted power law. Also see [5](#c04.xhtml#c04-bib-0005) for detailed discussions on the test.

## Empirical Analysis of Regional COVID-19 Case Figures

In what follows, we consider an empirical analysis of the regional COVID-19 case figures as of 11 May 2020 for 14 countries.

We focus on the column `R²` in [Table 4.7](#c04.xhtml#c04-tbl-0007), which is the `R²` statistic for the regression model ([4.13](#c04.xhtml#c04-disp-0050)). For all countries except China and Russia, `R²` exceeds 0.9, testifying to the presence of Zipf's law for the regional distribution of COVID-19 cases in a country.
