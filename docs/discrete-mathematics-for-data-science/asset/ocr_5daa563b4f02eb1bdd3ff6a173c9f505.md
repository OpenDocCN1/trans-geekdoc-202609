where \(x_{n_i}\) is the available number of data samples in the \(i^{th}\) independent variable, \(x_i\).

Over \(d\) dimensions, the least possible sample density can be computed as:

\(sample\ density = (s_{min}/s_{max})^d\)

where \(s_{min}\) is the minimum number of available samples from all independent variables and \(s_{max}\) is the maximum number of available samples from all independent variables. This worst case scenario is equivalent to the most possible sample sparsity. Based on that scenario, Figure 23.2 shows how sample density decreases as dimensions increase.

# TABLE 23.2 Sample densities, with constant sample size

| Dimensions | \(s_{min}\) | \(s_{max}\) | Density |
|---|---|---|---|
| 1 | 15 | 100 | 0.150 |
| 2 | 15 | 100 | 0.023 |
| 3 | 15 | 100 | 0.003 |