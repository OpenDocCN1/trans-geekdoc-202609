where

```
\(\widehat{Z_t / Z_{t-1}} = \frac{\sum_{i=1}^{N_s} \tilde{w}_t^i}{\sum_{i=1}^{N_s} \tilde{w}_{t-1}^i}\)
```

This estimate of the marginal likelihood is very useful for tasks such as parameter estimation.

# 13.2.4 Resampling methods

Importance sampling gives a weighted set of particles, \(\{(W_t^i, z_t^i) : i = 1 : N\}\), which we can use to approximate posterior expectations using

```
\(\mathbb{E}[f(z_t)|y_{1:t}] \approx \sum_{i=1}^N W_t^i f(z_t^i)\)
```

Suppose we sample a single index \(A \in \{1, \dots, N\}\) with probabilities \((W_t^1, \dots, W_t^N)\). Then the expected value evaluated at this index is

```
\(\mathbb{E}[f(z_t^A)|y_{1:t}] = \sum_{i=1}^N p(A=i)f(z_t^i) = \sum_{i=1}^N W_t^i f(z_t^i)\)
```

If we sample \(N\) indices independently and compute their average, we get

```
\(\mathbb{E}[f(z_t)|y_{1:t}, A_{1:N}] \approx \frac{1}{N} \sum_{i=1}^N f(z_t^{A_i})\)
```

which is a standard unweighted Monte Carlo estimate, with weights \(W_t^i = 1/N\). Averaging over the indices gives

```
\(\mathbb{E}_{A_{1:N}} \left[ \frac{1}{N} \sum_{i=1}^N f(z_t^{A_i}) \right] = \sum_{i=1}^N W_t^i f(z_t^i)\)
```

Thus using the output from the resampling procedure — which drops particles with low weight, and duplicates particles with high weight — will give the same result in expectation as the original weighted estimate. However, to reduce the variance of the method, we need to pick the resampling method carefully, as we discuss below.

# 13.2.4.1 Inverse cdf

Most of the common resampling methods work as follows. First we form the cumulative distribution from the weights \(W^{1:N}\), as illustrated by the staircase in Figure 13.4. (We drop the \(t\) index for brevity.) Then, given a set of \(N\) uniform random variables, \(U^i \sim \text{Unif}(0, 1)\), we check to see which bin (interval) \(U^i\) lands in; if it falls in bin \(a\), we return index \(a\), i.e., sample \(i\) gets mapped to index \(a\) if

```
\(\sum_{j=1}^{a-1} W^j \le U^i < \sum_{j=1}^a W^j\)
```