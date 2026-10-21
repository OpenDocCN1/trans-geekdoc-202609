# **Table 26A.1:** Seasonal index and seasonally adjusted EPS for J&J in terms of the first 12 quarters' data.

| Date | $x_t$ | $z_t^*$ | $x_t/z^*$ | Seasonal index | Seasonally adjusted EPS, $d_t$ |
|---|---|---|---|---|---|
| 2000.1 | 0.86 |  |  | 0.503173 | 1.709154 |
| 2 | 1.8 |  |  | 0.750721 | 2.397696 |
| 3 | 2.68 | 2.1775 | 1.230769 | 1.207303 | 2.219824 |
| 4 | 3.3 | 2.095 | 1.575179 | 1.538804 | 2.144523 |
| 2001.1 | 1 | 1.84875 | 0.540906 | 0.503173 | 1.987389 |
| 2 | 1 | 1.52375 | 0.656276 | 0.750721 | 1.332053 |
| 3 | 1.51 | 1.295 | 1.166023 | 1.207303 | 1.250722 |
| 4 | 1.87 | 1.26375 | 1.479723 | 1.538804 | 1.21523 |
| 2002.1 | 0.6 | 1.31 | 0.458015 | 0.503173 | 1.192433 |
| 2 | 1.15 | 1.37875 | 0.834089 | 0.750721 | 1.531861 |
| 3 | 1.73 |  |  | 1.207303 | 1.432946 |
| 4 | 2.2 |  |  | 1.538804 | 1.429682 |

# **Table 26A.2:** Calculation of seasonal indexes of EPS for J&J.

| Year | Quarter 1 | Quarter 2 | Quarter 3 | Quarter 4 | Sums |
|---|---|---|---|---|---|
| 2000 |  |  | 1.231 | 1.575 |  |
| 2001 | 0.541 | 0.656 | 1.166 | 1.480 |  |
| 2002 | 0.458 | 0.834 |  |  |  |
| Median | 0.499 | 0.745 | 1.198 | 1.527 | 3.970 |
| Seasonal Index | 0.503 | 0.751 | 1.207 | 1.539 | 4.000 |

12 values by means of simple time trend linear regression produces

$$\hat{d}_t = 2.192966 - 0.08298t$$

The value $\hat{b} = 0.08298$ becomes the initial trend estimate of $T_0$. Finally, the initial smoothed value for fourth quarter 1999 is

$$s_0 = [a + b(0)](\text{initial seasonal index for fourth quarter})$$ $$= (2.192996)(1.539) = 3.374543$$

This estimate of $s_0$ becomes the forecast value for each of the quarters in 2000, as indicated in column (6) of Table 26A.3.