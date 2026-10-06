# # Converting an input: inference

![](bbox=[0.001, 0.185, 0.468, 0.893])

+   - Compute the attention weights $w_i(1)$ over all inputs for the *second* output using $s_0$
  - Compute raw weights, followed by softmax
- Compute "context" $c_1$
  - Weighted sum of input hidden representations
- Input $c_1$ and first output word to the decoder
  - In practice we enter the *embedding* of the word

```
$g(h_i, s_0) = h_i^T W s_0$
$e_i(1) = g(h_i, s_0)$
w_i(1) = \frac{\exp(e_i(1))}{\sum_j \exp(e_j(1))}, c_1 = \frac{1}{N} \sum_i^N w_i(1)h_i$
```