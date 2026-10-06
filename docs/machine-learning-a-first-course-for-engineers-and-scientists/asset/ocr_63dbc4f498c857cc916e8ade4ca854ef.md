# 7.1 Bagging

# The bootstrap

As outlined in Example 7.1, the idea of bagging is to average over multiple base models, each learned from a different training dataset. We first have to construct different training datasets. In the best of worlds we would collect multiple datasets, but most often we cannot do that and instead we have to make the most out of the limited data available. For this purpose, the bootstrap is useful.

The bootstrap is a method for creating multiple datasets (of size $n$) out of one dataset (also of the real-world data generating process, in the sense that if $i$ were to collect more training data, the data points would likely be similar to the training data points already contained in $\mathcal{T}$. We can argue that randomly picking data points from $\mathcal{T}$ is a reasonable way to simulate a "new" training dataset. In statistical terms, instead of sampling from the population (collecting more data), we sample from available training data which is assumed to be a good representation of the population.

The bootstrap is stated in Algorithm 7.1 and illustrated in Example 7.2 below. Note that the sampling is done with replacement, meaning that the resulting bootstrapped dataset may contain multiple copies of some of the original training data points, whereas other data points are not included at all.

# Algorithm 7.1: The bootstrap.

```
Data: Training dataset $\mathcal{T} = \{\mathbf{x}_i, y_i\}_{i=1}^n$
Result: Bootstrapped dataset $\hat{\mathcal{T}} = \{\hat{\mathbf{x}}_i, \hat{y}_i\}_{i=1}^n$
1 for $i = 1, \dots, n$ do
2   Sample $t$ uniformly from the set of integers $\{1, \dots, n\}$
3   $\hat{\mathbf{x}}_i = \mathbf{x}_t$ and $\hat{y}_i = y_t$
4 end
```

> Time to reflect 7.1: What would happen if the sampling was done without replacement in the bootstrap?