# Gene Expression Pattern Discovery

is selected as an integer between two and the length of y. A MOST $t$ statistic is defined as below, where $\sigma_{	heta(1:k)}$ stands for the standard deviation between the first value and $k^{th}$ value within the $\vartheta$ vector,

```
$t^{MOST} = \max_{\forall k} \left\ \frac{\sqrt{\sum_{i=1}^{k}(y_i - \mu_x)^2}}{\sigma_{\theta(1:k)}} \right\$ (6.14)
```

The MOST $p$ value is also calculated using the permutation approach.

# 6.4.6 LSOSS

The least sum of ordered subset square $t$ statistic algorithm (LSOSS) is a different method to calculate a $t$ statistic based on MOST [Wang and Rekaya, 2010]. The LSOSS $t$ statistic is calculated in two steps. In the first step, an optimal cutting point is sought by examining the best separation of a vector of the case expressions in terms of a standard deviation. The vector of the case expressions is sorted and a cutting point is varied between two and the length of the vector minus two. For every potential cutting point, two standard deviations are calculated. The sum of these two standard deviations is believed to reach a maximum at one of varying cutting points. Suppose the optimal cutting point is denoted by $k^*$, the optimal deviation sum at the optimal cutting point is denoted by $\sigma_y^*$. At this optimal cutting point, a LSOSS $t$ statistic is calculated using the following equation, where $n$ and $m$ are the lengths of two vectors, $x$ and $y$, respectively,

```
$t^{LSOSS} = \frac{k^*(\mu_{y(1:k^*)}) - \mu_x)}{(\sigma_x + \sigma_y^*)/(n + m - 2)}$ (6.15)
```

# 6.4.7 DOG

The basic assumption of the algorithm, which is named as discovering outliers based on the tight Gaussian cluster (DOG), is that the majority of the control expressions should have a small variance. Therefore, they form an initial tight Gaussian cluster [Yang and Yang, 2013]. It is assumed in