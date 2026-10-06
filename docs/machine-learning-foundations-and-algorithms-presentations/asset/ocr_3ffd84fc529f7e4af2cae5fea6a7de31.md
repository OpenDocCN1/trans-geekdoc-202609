# Maximum Likelihood Estimation (MLE)

Log-likelihood is easier to optimize:

```
loglik(\theta; D) = \sum_{i} \log p_{\theta}(x_i, y_i)
```

+   - Log is monotonous -> same optimum
- Sums are “nicer” to optimize than products
- Log cancels exponential form (most distributions are in the exponential family)

The MLE solution is given by:

```
\theta_{ML} = \text{argmax}_{\theta} \text{loglik}(\theta; D)
```