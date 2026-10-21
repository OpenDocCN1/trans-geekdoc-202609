# Table 51.9: Comparison of numerical accuracy between the CEV and the SV models (deep in-the-money put option).

| Time (s) | CEV N analytic | Price 57.99747 | Error | N,M analytic | SV price 57.99747 | Error |
|---|---|---|---|---|---|---|
| 0.1 | 1434 | 57.99623 | -0.00124 |  |  |  |
| 0.2 | 1984 | 57.99584 | -0.00163 | 10 | 48.40058 | -9.59689 |
| 0.5 | 2953 | 57.99688 | -0.00059 | 24 | 55.76441 | -2.23305 |
| 1 | 3706 | 57.99656 | -0.00091 | 48 | 57.47296 | -0.52451 |
| 2 | 4574 | 57.99745 | -0.00002 | 86 | 57.82273 | -0.17474 |
| 5 |  |  |  | 184 | 57.95248 | -0.04499 |
| 10 |  |  |  | 265 | 57.97286 | -0.02461 |
| 20 |  |  |  | 361 | 57.98215 | -0.01532 |
| 50 |  |  |  | 522 | 57.98858 | -0.00889 |
| 100 |  |  |  | 678 | 57.99134 | -0.00613 |
| 200 |  |  |  | 869 | 57.99313 | -0.00434 |

# Table 51.10: Comparison of computational efficiency between the CEV and the SV models (deep in-the-money put option).

| Put error | CEV X=350 N | CPU time (s) | Put error | SV X=350 N,M | CPU time (s) |
|---|---|---|---|---|---|
| 0.01 | 348 | 0.016 | 0.01 | 477 | 39.563 |
| 0.005 | 423 | 0.016 | 0.005 | 779 | 146.563 |
| 0.001 | 4286 | 1.625 | 0.001 | 2800-2900 | >9050.344 |

the CEV model is robust across different values of β. The longest time to reach $0.0005 absolute pricing error in our experiment is merely 0.75 s in pricing deep in-the-money put with β equals to 0 and −1. Therefore, we can conclude that the trinomial method of the CEV process by Boyle and Tian (1999) in terms of numerical efficiency is robust enough for the empirical study.

Finally, we should note that the algorithms of American option pricing for these two numerical methods are similar to their European cases, except for the additional step for checking the early exercise possibility at each time step. Therefore, the time for pricing American-style option is expected to be longer than that of the European option.