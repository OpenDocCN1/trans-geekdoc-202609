Table 8.2 Performance indices for single-wake scenario.

| Model | Metric | 2.5D0 | 3D0 | 5D0 |
|---|---|---|---|---|
| Jensen | RMSE | 3.7865 | 3.5461 | 2.7769 |
| | R² | 0.8628 | 0.8683 | 0.8605 |
| Frandsen | RMSE | 1.0668 | 0.9375 | 2.7769 |
| | R² | 0.8885 | 0.8780 | 0.8964 |
| Proposed | RMSE | 0.7148 | 0.7146 | 0.7169 |
| | R² | 0.8976 | 0.8823 | 0.8971 |

![](bbox=[0.12, 0.27, 0.83, 0.46])

# Figure 8.4 Wake effect on WT2 based on the proposed and benchmark models.

Based on the RMSE, the proposed bilateral Gaussian wake model outperforms Jensen's model by 81.11% and Frandsen's model by 32.99% for a downstream distance of 2.5D0.

# 8.2.4 Multiple-wake model

This study can be further extended for wind wakes due to multiple up-wind turbines. Due to shadowing effect created by wind turbines placed at different locations, the effective wind speed in the presence of wakes using Jensen's model [31] is

```
u = u_0 \left( 1 - \sum_{i=1}^N \left( 1 - \sqrt{1 - C_t \left( \frac{r_0}{r_{ij}} \right)^2} \frac{A_{sh,i}}{A_0} \right) \right), (8.19)
```

where \(A_{sh,i}\) is the overlap area experienced by wind turbine under shadow from upwind turbine, and

```
A_{sh,i} = r_0^2 \cos^{-1} \left( \frac{d_{ij}^2 + r_0^2 - r_{ij}^2}{2 d_{ij} r_0} \right) + r_{ij}^2 \cos^{-1} \left( \frac{d_{ij}^2 + r_{ij}^2 - r_0^2}{2 d_{ij} r_{ij}} \right)
```