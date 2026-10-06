# Converting an input: inference

+   Compute the attention weights $w_i(0)$ for the first output using $s_{-1}$

+   - Will be a distribution over the input words

+   Compute "context" $C_0$

+   - Weighted sum of input hidden states

+   Input $c_0$ and $<sos>$ to the decoder at time 0

+   - $<sos>$ because we are starting a new sequence

+   - In practice we will enter the *embedding* of $<sos>$

![](bbox=[0.011, 0.173, 0.376, 0.663])

```
$g(h_i, s_{-1}) = h_i^T W_g s_{-1}$
$e_i(0) = g(h_i, s_{-1})$
w_i(0) = \frac{\exp(e_i(0))}{\sum_j exp(e_j(0))}$
```