# # The self-attention block

We can have multiple such “heads”

+   - Each will have an independent set of queries, keys and values
- Each will obtain an independent set of attention weights
  - Potentially focusing on a different aspect of the input than other heads
- Each component computes an independent output

The final output is the concatenation of the outputs of these attention heads

“MULTI-HEAD ATTENTION” (actually Multi-head self attention)

```
$q_i^a = W_q^a h_i$
k_i^a = W_k^a h_i$
v_i^a = W_v^a h_i$
w_{ij}^a = attn(q_i^a, k_{0:N}^a)$n$o_i^a = \sum_j w_{ij}^a v_j^a$
```

![](bbox=[0.613, 0.148, 0.976, 0.768])