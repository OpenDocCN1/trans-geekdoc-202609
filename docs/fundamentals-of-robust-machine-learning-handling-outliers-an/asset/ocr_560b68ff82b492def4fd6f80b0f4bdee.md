![](bbox=[0.167, 0.106, 0.531, 0.365])

**Figure 7.2** The crossing problem occurs when a higher quantile (76th percentile) has fewer points below it compared to a lower quantile (75th percentile).

manifests itself as a non-monotonicity problem as percentiles increase. But why would this occur? We will explore this question in the next section.

> Note: We emphasize here that the lines and hyperplanes from quantile regression will always intersect in some way if they are not parallel. However, the model can still be viewed as acceptable if the crossing occurs outside the convex hull. Lines crossing within the convex hull often leads to non-monotonicity, but not always, whereas if non-monotonicity is detected, there is implicitly a crossing problem inside the convex hull. Therefore, we need a way to monitor any non-monotonic behavior in quantile regression to evaluate the performance of different approaches.

# ## 7.4 Standard Quantile Loss Function

Quantile regression is described in this section starting with the original method for studying the effect of explanatory variables on the entire conditional distribution of the response variable. It has been used extensively since the initial concepts were developed in the late 1970s and early 1980s. It is based on the so-called check function whereby the quantile of interest is obtained by setting a parameter, \(\tau\).

Different regression quantiles (RQ) represented by lines or hyperplanes are obtained by minimizing the conditional loss function in M-estimator form given by,

```
\(J^{RQ}(\beta|\tau) = \sum_{i=1}^n \rho_{RQ}(r_i; \tau), \quad (7.4.1)\)
```

with

```
\(\rho_{RQ}(r_i; \tau) = \left\{\begin{array}{ll} -(1-\tau)r_i & \text{if } r_i < 0 \\ \tau r_i & \text{if } r_i \ge 0 \end{array}\right., \quad (7.4.2)\)
```