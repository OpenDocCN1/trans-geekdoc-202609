# Chapter 7 Graphs

$Q_k[i][j] = the smaller of the length of the preceding path from $V_i$ to $V_j$ or the sum of the lengths of the preceding paths from $V_i$ to $V_k$ and from $V_k$ to $V_j$.

More exactly,
$Q_k[i][j] = \min (Q_{k-1}[i][j], Q_{k-1}[i][k] + Q_{k-1}[k][j])$

The initial matrix $Q_0$ is the same as the weight matrix $W$ except that each 0 in $W$ is replaced by $\infty$ or a very, very large number. The final matrix $Q_n$ will be the desired matrix $Q$.

**Example**: let us take a graph and find the values of $Q_0, Q_1, Q_2, Q_3, Q_4$

# **Solution**

Weighted adjacency matrix for this graph is

| | V1 | V2 | V3 | V4 |
|---|---|---|---|---|n| **W** | V1 | 0 | 2 | 0 | 9 |
| | V2 | 3 | 0 | 4 | 7 |
| | V3 | 0 | 6 | 0 | 2 |
| | V4 | 14 | 0 | 4 | 0 |

| | V1 | V2 | V3 | V4 |
|---|---|---|---|---|n| **$Q_0$** | V1 | $\infty$ | 2 | 0 | 9 |
| | V2 | 3 | $\infty$ | 4 | 7 |
| | V3 | $\infty$ | 6 | $\infty$ | 2 |
| | V4 | 14 | $\infty$ | 4 | $\infty$ |

| | V1 | V2 | V3 | V4 |
|---|---|---|---|---|n| | V1 | V1V2 | -- | V1V4 |
| | V2 | V2V1 | -- | V2V3 | V2V4 |
| | V3 | V3V2 | -- | V3V4 |
| | V4 | V4V1 | -- | V4V3 |

After including node V1 (k=1)

| | V1 | V2 | V3 | V4 |
|---|---|---|---|---|n| **$Q_1$** | V1 | $\infty$ | 2 | 0 | 9 |
| | V2 | 3 | 5 | 4 | 7 |
| | V3 | $\infty$ | 6 | $\infty$ | 2 |
| | V4 | 14 | 16 | 4 | 23 |

![](bbox=[0.673, 0.173, 0.882, 0.283])