
## Table 57.4: Classification using Fisher's discriminant analysis.

| Predicted rating | Aa | A | Baa | Ba | B | Total |
|---|---|---|---|---|---|---|
| IN-SAMPLE |  |  |  |  |  |  |
| Aa | 9 | 2 | 0 | 0 | 0 | 11 |
| A | 2 | 14 | 2 | 0 | 0 | 18 |
| Baa | 0 | 1 | 12 | 2 | 0 | 15 |
| Ba | 0 | 0 | 1 | 22 | 0 | 23 |
| B | 0 | 0 | 0 | 0 | 17 | 17 |
| Total | 11 | 17 | 15 | 24 | 17 | 84 |
| OUT-SAMPLE |  |  |  |  |  |  |
| Aa | 2 | 0 | 3 | 0 | 0 | 5 |
| A | 1 | 8 | 3 | 0 | 0 | 12 |
| Baa | 0 | 1 | 4 | 0 | 0 | 5 |
| Ba | 0 | 0 | 0 | 16 | 2 | 18 |
| B | 0 | 0 | 0 | 4 | 4 | 8 |
| Total | 3 | 9 | 10 | 20 | 6 | 48 |

## Table 57.5: Coefficients and explained variances of stepwise discriminant functions.

| Discriminant functions | D1 | D2 | D3 | D4 |
|---|---|---|---|---|
| Coefficients | Σ^{-1/2} ξ1 | Σ^{-1/2} ξ2 | Σ^{-1/2} ξ3 | Σ^{-1/2} ξ4 |
| Subordination: X1 | -1.9761 | 0.6120 | -0.4248 | 0.5034 |
| Years of Consecutive Dividend: X9 | 0.7042 | 1.2120 | 0.3283 | 0.3072 |
| Issue Size: X16 | 0.3648 | -0.3528 | -0.7618 | -0.0619 |
| Net Income and Interest/Interest: Mean: X24 | 0.0230 | -0.7098 | 0.0173 | 0.8207 |
| Long-Term Debt/Total Assets: Mean: X25 | -0.4076 | -0.4587 | 0.6801 | -0.2551 |
| Net Income/Total Assets: X35 | 0.0320 | 0.0543 | -0.4591 | -0.3849 |
| Variance | 1.5725 | 0.6039 | 0.6891 | 0.8261 |
| Cumulative percentage of total variance | 4.49% | 1.72% | 1.97% | 2.36% |

D1 = ξ1' Σ^{-1/2} X, ..., D4 = ξ4' Σ^{-1/2} X are presented in Table 57.5. From Table 57.5, the first discrimination function D1 is mostly related to the financial variables: Subordination (X1). The second discriminant function D2 is mostly related to: Years of consecutive dividend (X9), Net income and interest /interest: mean (X24). The third discriminant function D3 is mostly related to: Issue size (X16) and Net Income/Total Assets (X35). Finally, the fourth discriminant function D4 is mostly related to: Long-term debt/total assets: mean (X25).

## Table 57.6: Classification using stepwise discriminant analysis.

| Predicted rating | Aa | A | Baa | Ba | B | Total |
|---|---|---|---|---|---|---|
| **Actual rating** |  |  |  |  |  |  |
| **IN-SAMPLE** |  |  |  |  |  |  |
| Aa | 8 | 3 | 0 | 0 | 0 | 11 |
| A | 3 | 12 | 2 | 0 | 0 | 17 |
| Baa | 0 | 2 | 10 | 8 | 0 | 20 |
| Ba | 0 | 0 | 3 | 10 | 4 | 17 |
| B | 0 | 0 | 0 | 6 | 13 | 19 |
| Total | 11 | 17 | 15 | 24 | 17 | 84 |
| **OUT-SAMPLE** |  |  |  |  |  |  |
| Aa | 1 | 0 | 0 | 0 | 0 | 1 |
| A | 1 | 8 | 6 | 0 | 0 | 15 |
| Baa | 1 | 1 | 4 | 0 | 0 | 6 |
| Ba | 0 | 0 | 0 | 16 | 1 | 17 |
| B | 0 | 0 | 0 | 4 | 5 | 9 |
| Total | 3 | 9 | 10 | 20 | 6 | 48 |

In Table 57.5, the explanatory powers of the four discriminant functions $D_1,\dots,D_4$ are 4.49%, 1.72%, 1.97%, and 2.36%, respectively. Table 57.6 presents the classification of the 84 in-sample and 48 out-sample bonds into one of the 5 ratings B, Ba, Baa, A, Aa using the four stepwise discriminant functions $D_1,\dots,D_4$. In Table 57.9, the in-sample explanatory and discriminant powers of the four stepwise discriminant functions $D_1,\dots,D_4$ are 10.55% and 63.10%, respectively; while the out-sample explanatory and discriminant powers of $D_1,\dots,D_4$ are 10.37% and 70.83%, respectively.

## 57.4.4 Credit-scoring model based on hybrid of PCA and FDA using GP approach

In the predictive model HDA, four discriminant functions $M_1,\dots,M_4$ are found by solving the MINIMAX goal programming defined in (57.8)-(57.9) one by one. For the discriminant functions $M_1$, $M_2$, $M_3$, and $M_4$, the exponent $v$ in (57.10) are estimated to be 3.9, 1.2, 2.2, and 1.4, respectively. The target Pareto point $Q$ in (57.11) are (2.42, 1.67), (1.72, 1.70), (0.73, 1.097), (0.6, 1.54), respectively. By selecting a starting solution $\boldsymbol{\xi}^0 = \boldsymbol{u}_1$, where $\boldsymbol{u}_1$ is the eigenvector corresponding to the matrix $W_2$ in (57.7), the primal method is used to find $\boldsymbol{\xi}^*$ that minimizes the distance between $P^* = (g_1(\boldsymbol{\xi}^*), g_2(\boldsymbol{\xi}^*))$ and $Q$. In the primal approach, a direction $\boldsymbol{d}$ is chosen with step size $\Delta$

so that the distance between $ξ^j = ξ^{j−1} + Δd$ and $Q$ is reduced. The algorithm converges at the 218th step with $P^* = (2.36, 1.73)$, the 294th step at $P^* = (1.65, 1.61)$, the 595th at $P^* = (0.71, 1.082)$, and the 530th at $P^* = (0.61, 1.55)$ with the distance $(QP^*)$ at 0.0823, 0.1199, 0.020, 0.013, respectively. The coefficients of $M_i = ξ_i'Σ^{-1/2}$ are listed in Table 57.7. From Table 57.7, the first multiple-objective discrimination function $M_1$ is mostly related to the five financial variables: Subordination ($X_1$), Sales/net worth ($X_5$), Years of consecutive dividend ($X_9$), Long-Term Debt/Total Assets ($X_{10}$), Issue size ($X_{16}$), number of shares of common stock ($X_{17}$), Net income and interest/Interest: mean ($X_{24}$). The second multiple-objective discriminant function M2 is mostly related to the third multiple-objective discriminant function M3, which is mostly related to: Market value of common stock/long-term debt ($X_{18}$), Net income: CV ($X_{19}$), Long-term debt/total assets: mean ($X_{25}$), Market value of common stock/long-term debt: mean ($X_{31}$). For the fourth discriminant function $M_4$, the related variables are: Total assets ($X_2$), Net working capital/Sale ($X_3$), Net worth/total assets ($X_4$), Net working capital ($X_{13}$), Sales ($X_{14}$), Issue sizes ($X_{16}$), Net income/total assets: CV ($X_{22}$), Total assets: mean ($X_{23}$).

In Table 57.7, the explanatory powers of the four hybrid discriminant functions $M_1, …, M_4$ are 2.91%, 7.63%, 1.01%, and 0.24%, respectively. Table 57.8 presents the classification of the 84 in-sample and 48 out-sample bonds into one of the 5 ratings B, Ba, Baa, A, Aa using the hybrid discriminant functions $M_1, …, M_4$. In Table 57.9, the in-sample explanatory and discriminant powers of the four discriminant functions $M_1, …, M_4$ are 11.79% and 85.71%, respectively; while the out-sample explanatory and discriminant powers of $M_1, …, M_4$ are 11.65% and 75.00%, respectively.

## 57.4.5 Comparison of the four credit-scoring models

The comparison of the four predictive models, namely, PC, FDA, SDA, and HDA, are presented in Table 57.9. For the in-sample bonds, one sees that there is no single approach which outperforms all the other alternatives by its explanatory power as well as discriminant power simultaneously. The principle component analysis provides the highest explanatory power but has very poor discriminant power. On the contrary, Fisher’s discriminant analysis provides the highest discriminant power but very poor explanatory power. The stepwise discriminant analysis by Pinches and Mingo (1973) provides both unsatisfactory explanatory and discriminant powers. While the hybrid model developed in this study provides very satisfactory discriminant power (almost close to the discriminant power by Fisher’s discriminant analysis).

## Table 57.7: Coefficients and explained variances of hybrid discriminant functions.

| Discriminant function | $M_1$ | $M_2$ | $M_3$ | $M_4$ |
|---|---|---|---|---|
| Coefficients | $\Sigma^{-1/2}\xi_1$ | $\Sigma^{-1/2}\xi_2$ | $\Sigma^{-1/2}\xi_3$ | $\Sigma^{-1/2}\xi_4$ |
| Subordination: $X_1$ | -2.1661 | 0.1572 | 0.5854 | -0.4208 |
| Total Assets: $X_2$ | 0.3343 | 0.0470 | -0.5426 | -1.0671 |
| Net Working Capital/Sale: $X_3$ | 0.3992 | -0.0404 | 0.0666 | -1.1885 |
| Net Worth/Total Assets: $X_4$ | 0.1180 | -0.1625 | 0.0997 | -0.7823 |
| Sales/Net Worth: $X_5$ | -1.4332 | 0.3093 | 0.1968 | 0.0835 |
| Net Income/Sales: $X_6$ | -0.1460 | -0.1763 | -0.0639 | 0.1282 |
| Recent Market High of Debt: $X_7$ | -0.1797 | -0.0065 | -0.1835 | -0.1714 |
| Price/Earnings: $X_8$ | 0.5117 | 0.0073 | -0.4098 | -0.2280 |
| Years of Consecutive Dividend: $X_9$ | 1.2557 | -0.0166 | -0.0580 | -0.0542 |
| Long-Term Debt/Total Assets: $X_{10}$ | -1.2879 | -0.0142 | 0.1986 | 1.2072 |
| Sales/Total Assets: $X_{11}$ | 0.6665 | 0.2039 | -0.3423 | 0.4627 |
| Net Income/Net Worth: $X_{12}$ | 0.9497 | -0.071 | -0.4368 | 0.0346 |
| Net Working Capital: $X_{13}$ | -0.1150 | 0.1525 | -0.2300 | 0.8428 |
| Sales: $X_{14}$ | 0.3955 | 0.1698 | 0.1491 | -1.9448 |
| Earnings per Share: $X_{15}$ | 0.2651 | 0.0026 | -0.2251 | -0.0120 |
| Issue Size: $X_{16}$ | -0.4856 | 0.0943 | 0.2986 | -0.0643 |
| Common Stock Share Number: $X_{17}$ | 0.7329 | 0.0048 | -0.0569 | 0.0381 |
| Market Value of Common Stock /Long-Term Debt: $X_{18}$ | 0.0616 | 0.0196 | 0.2629 | -0.1717 |
| Net Income: CV: $X_{19}$ | 0.2349 | -0.0075 | -0.6601 | 0.3593 |
| Long-Term Debt/Net Worth: Mean: $X_{20}$ | -0.2378 | -0.0648 | -0.0539 | -0.0169 |
| Net Income/Total Assets: Mean: $X_{21}$ | -0.0585 | 0.0086 | 0.0257 | -0.2311 |
| Net Income/Total Assets: CV: $X_{22}$ | -0.4235 | -0.003 | 0.2613 | -0.6118 |
| Total Assets: Mean: $X_{23}$ | -0.0620 | 0.0763 | 0.5421 | 1.6762 |
| Net Income and Interest/Interest: Mean: $X_{24}$ | -1.0240 | 0.0459 | 0.2021 | -0.1270 |
| Long-Term Debt/Total Assets: Mean: $X_{25}$ | 0.0041 | -0.1076 | 0.2495 | 0.0058 |
| Sales/Total Assets: Mean: $X_{26}$ | -0.1709 | 0.1564 | 0.1198 | 0.1304 |
| Long-Term Debt/Total Assets: CV: $X_{27}$ | 0.6775 | -0.0149 | -0.2705 | 0.3277 |
| Net Income and Interest/Interest: CV: $X_{28}$ | 0.4794 | 0.0011 | -0.3486 | -0.5129 |
| Market Price Change: CV: $X_{29}$ | -0.2218 | 0.0444 | 0.2105 | -0.1786 |
| Earnings per Share Change: CV: $X_{30}$ | 0.0535 | 0.0009 | -0.2426 | 0.0138 |
| Market Value of Common Stock /Long-Term Debt: Mean: $X_{31}$ | -0.2934 | 0.0572 | 0.5163 | 0.2161 |
| Sales Percentage Change: Mean: $X_{32}$ | -0.0755 | -0.0471 | 0.0279 | -0.1206 |
| Net Income Percentage Change: Mean: $X_{33}$ | 0.1742 | -0.0188 | -0.0045 | -0.0862 |
| Long-Term Debt/Net Worth: $X_{34}$ | 0.6455 | -0.1140 | -0.4517 | -0.9547 |
| Net Income/Total Assets: $X_{35}$ | -0.1980 | 0.0071 | -0.0774 | -0.0522 |
| Variance | 1.0203 | 2.6715 | 0.3523 | 0.0834 |
| Cumulative percentage of total variance | 2.91% | 7.63% | 1.01% | 0.24% |
