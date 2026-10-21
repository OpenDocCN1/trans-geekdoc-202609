# Table 74.4: Simulation results of six estimators.

| Stat | Mean | Median | Std | Bias | Bias/True value (%) | RMSE | RMSE/True value (%) | % of non-positive estimates |
|---|---|---|---|---|---|---|---|---|
| T = 60 |  |  |  |  |  |  |  |  |
| Ŝ² | 0.8865 | 0.8323 | 0.3425 | 0.8153 | 1145.9229 | 0.8843 | 1242.9086 | 0 |
| Ŝ²_less_biased | 0.1224 | 0.0804 | 0.2244 | 0.0513 | 72.0500 | 0.2302 | 323.4968 | 33 |
| Ŝ²_less_biased+ | 0.1706 | 0.1120 | 0.1940 | 0.0994 | 139.7276 | 0.2180 | 306.4268 | 17 |
| Ŝ²_Bayes | 0.1614 | 0.1008 | 0.1823 | 0.0903 | 126.8787 | 0.2035 | 285.9582 | 0 |
| Ŝ²_mixed | 0.1790 | 0.1197 | 0.1904 | 0.1078 | 151.5211 | 0.2188 | 307.5031 | 0 |
| Ŝ²_adj | 0.2660 | 0.2347 | 0.1636 | 0.1948 | 273.8199 | 0.2544 | 357.5133 | 0 |
| T = 120 |  |  |  |  |  |  |  |  |
| Ŝ² | 0.3910 | 0.3769 | 0.1217 | 0.2957 | 310.3521 | 0.3198 | 335.6144 | 0 |
| Ŝ²_less_biased | 0.3619 | 0.3486 | 0.1144 | 0.2908 | 408.6682 | 0.3125 | 439.1837 | 19 |
| Ŝ²_less_biased+ | 0.0840 | 0.0724 | 0.0943 | 0.0128 | 18.0507 | 0.0952 | 133.8142 | 6 |
| Ŝ²_Bayes | 0.0972 | 0.0796 | 0.0832 | 0.0260 | 36.5963 | 0.0872 | 122.5928 | 0 |
| Ŝ²_mixed | 0.0580 | 0.0427 | 0.0542 | -0.0131 | -18.4153 | 0.0558 | 78.3911 | 0 |
| Ŝ²_adj | 0.0983 | 0.0805 | 0.0826 | 0.0271 | 38.1019 | 0.0869 | 122.1181 | 0 |
| T = 240 |  |  |  |  |  |  |  |  |
| Ŝ² | 0.1978 | 0.1918 | 0.0554 | 0.1266 | 177.9970 | 0.1382 | 194.2978 | 0 |
| Ŝ²_less_biased | 0.0756 | 0.0697 | 0.0509 | 0.0045 | 6.2706 | 0.0511 | 71.7877 | 5 |
| Ŝ²_less_biased+ | 0.0779 | 0.0704 | 0.0484 | 0.0067 | 9.4582 | 0.0488 | 68.6557 | 0 |
| Ŝ²_Bayes | 0.0389 | 0.0326 | 0.0287 | -0.0323 | -45.3918 | 0.0432 | 60.7568 | 0 |
| Ŝ²_mixed | 0.0780 | 0.0704 | 0.0483 | 0.0068 | 9.6157 | 0.0488 | 68.5314 | 0 |
| Ŝ²_adj | 0.1081 | 0.1019 | 0.0461 | 0.0370 | 51.9732 | 0.0591 | 83.1152 | 0 |
| T = 600 |  |  |  |  |  |  |  |  |
| Ŝ² | 0.1183 | 0.1167 | 0.0267 | 0.0471 | 66.2594 | 0.0542 | 76.1236 | 0 |
| Ŝ²_less_biased | 0.0727 | 0.0713 | 0.0259 | 0.0016 | 2.1894 | 0.0259 | 36.4079 | 0 |
| Ŝ²_less_biased+ | 0.0727 | 0.0713 | 0.0258 | 0.0016 | 2.2360 | 0.0258 | 36.3270 | 0 |
| Ŝ²_Bayes | 0.2994 | 0.0298 | 10.115 | 0.2282 | 320.7808 | 10.117 | 14219.2582 | 0 |
| Ŝ²_mixed | 0.0727 | 0.0713 | 0.0258 | 0.0016 | 2.2360 | 0.0258 | 36.3270 | 0 |
| Ŝ²_adj | 0.0837 | 0.0821 | 0.0249 | 0.0126 | 17.6795 | 0.0279 | 39.1860 | 0 |

Notes: This table reports simulation results of six estimators by assuming the following parameters from the US whole sample period (taken from Table 74.1): (ψ² = 0.043037, μ_g = 0.007426, σ_g = 0.044291, S² = 0.071148). We present the mean, median, standard deviation, bias, percentage bias, root mean squared error, percentage root mean squared error, and the percentage incidence of non-positive estimates. We run the simulation by assuming N = 25 and T = 60, 120, 240, or 600.

comparable bias and RMSE with Ŝ²_less_biased+, so they are better choices. As for the estimator Ŝ²_adj from the adjusted minimum variance frontier, we can see that its bias is above 250% and median is almost 3 times of the true value. The reason for its inferior performance is that this estimator aims to reduce bias in estimating 1/ψ² but not ψ².