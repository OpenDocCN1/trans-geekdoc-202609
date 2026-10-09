6.18 on all 1.6 million observations. Unlike in the subsample, this should be plenty of data to get precise MLE HTE estimates.

```
```text
> fulIHte <- gamlr(x=cBind(d,controls),
+                  y=log(wber$MOVE), lambda.start=0)
```
```

Although the full sample MLE elasticities are not the “truth,” they are pretty darn close under the assumption of conditional ignorability.22 Figure 6.6 plots these full sample MLEs against the subsample estimates from Figures 6.3–6.5. The orthogonal ML estimates are (by far) closest; they appear roughly unbiased and, in an simple linear regression, explain more than 40% of the variation in the gold-standard estimates. In contrast, the naive lasso and MLE estimates of model Equation 6.18 explain only 15% and 1% of this variation. The naive lasso results are severely biased, and the MLE estimates are mostly noise.

![](bbox=[0.17, 0.4, 0.87, 0.63])

**FIGURE 6.6**: Comparison of elasticity estimates on the *n* = 5000 subsets to MLE results on the full 1.6 million observations. Each panel reports *R*2 values for OLS regression of subsample estimates on full values.

# SYNTHETIC CONTROLS

To conclude this chapter on controls, we will introduce a simple strategy for causal inference that is commonly used to evaluate large-scale business policy decisions. In this setting, you have a set of *units* of aggregation—for example, geographic regions or product classes—and only one or two of these units are treated. For example, you might be rolling out a new sales