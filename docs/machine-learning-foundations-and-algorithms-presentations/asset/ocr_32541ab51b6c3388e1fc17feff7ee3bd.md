# # Requirements on attention weights

* The weights $w_i(t)$ must be positive and sum to 1

+   - I.e. be a distribution
- Ideally, must be high for the most relevant inputs for the ith output and low elsewhere

![](bbox=[0.468, 0.105, 0.978, 0.545])

* Solution: A two step weight computation

+   - First compute raw weights: $e_i(t) = g(h_i, s_{t-1})$
- Then softmax them: $w_i(t) = \frac{\exp(e_i(t))}{\sum_j \exp(e_j(t))}$

# ### Typical options for g()
(variables in red must be learned)

```
$g(h_i, s_{t-1}) = h_i^T s_{t-1}$
$g(h_i, s_{t-1}) = h_i^T W s_{t-1}$
$g(h_i, s_{t-1}) = MLP([h_i, s_{t-1}])$
```