![](bbox=[0.15, 0.1, 0.89, 0.55])

**Figure 3.1** Key shrinkage R-estimators to be considered.

```
$$ \mathcal{L}_n = \left( \frac{\sqrt{n} \hat{\theta}_n^{UR}}{\hat{\eta}} \right)^2. $$
```

In the figure, we use the values \(\hat{\theta}_n^{UR} = 1.0, \hat{\eta} = 0.8, n = 64\) and \(\mathcal{L}_n = 100\).

We can now begin our cursory look at the shrinkage R-estimators starting with the hard threshold R-estimator, as follows

```
$$ \hat{\theta}_n^{HTR}(\lambda) = \hat{\theta}_n^{UR} I(\mathcal{L}_n > \lambda^2). $$
```

This estimator is also called the preliminary test subset selector R estimator (PTSSRE). Note that the hard-threshold estimator chooses \(\hat{\theta}_n^{UR}\) or 0 as the estimate based on the decision of the indicator function \(I(\cdot)\). As we can see in the top-left plot of Figure 3.1, when \(\lambda\) reaches the threshold of \(\sqrt{\mathcal{L}_n}\), the estimate shrinks abruptly from \(\hat{\theta}_n^{UR}\) to 0. This is where the name "hard threshold" comes from.