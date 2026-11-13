![](bbox=[0.26, 0.06, 0.73, 0.33])

# FIGURE 10.7: Simple tree.

The model depicted in Figure 10.7 only has 4 clusters, which means that the predictions can only take four values. The smallest one is 0.011 and encompasses a large portion of the sample (85%) and the largest one is 0.062 and corresponds to only 4% of the training sample.
We are then able to compute the bias and the variance of the predictions on the *testing* set.

```
mean(predict(fit_tree_simple, testing_sample) - testing_sample$R1M_Usd) # Bias
```

```
## [1] 0.004973917
```

```
var(predict(fit_tree_simple, testing_sample)) # Variance
```

```
## [1] 0.0001398003
```

On average, the error is slightly positive, with an overall overestimation of 0.005. As expected, the variance is very small (10⁻⁴).

For the complex model, we take the boosted tree that was obtained in Section 6.4.6 (fit_xgb). The model aggregates 40 trees with a maximum depth of 4, it is thus undoubtedly more complex.

```
mean(predict(fit_xgb, xgb_test) - testing_sample$R1M_Usd) # Bias
```

```
## [1] 0.00324996
```

```
var(predict(fit_xgb, xgb_test)) # Variance
```

```
## [1] 0.002206797
```

The bias is indeed smaller compared to that of the simple model, but in exchange, the variance increases substantially. The net effect (via the *squared bias*) is in favor of the simpler model.