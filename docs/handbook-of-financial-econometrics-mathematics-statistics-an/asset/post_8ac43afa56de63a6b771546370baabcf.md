
mean (X31), and Long-term debt/net worth (X34). The third principle component Y3 is related to the three financial variables: Net worth/total assets (X4), Sales/net worth (X5), Sales/total assets (X11), Sales (X14), Sales/total assets: mean (X26). The fourth principle component Y4 is related to the two financial variables: Net working capital/sale (X3), Net working capital (X13). The fifth principle component Y5 is related to the three financial variables: Price/earnings (X8), Net income/net worth (X12), Net income: CV (X19), Net income/total assets: mean (X21), Net income/total assets: CV (X22), Net income and interest/interest: mean (X24), Net income and interest/interest: CV (X28).

From Table 57.1, the 5 principle components Y1,…,Y5 account for 19.02%, 13.60%, 8.80%, 6.87%, and 6.58%, respectively, of the total variability of the original 35 financial variables. The classification of the 84 in-sample bonds into one of the 5 ratings B, Ba, Baa, A, Aa using the 5 principle components Y1,…,Y5 are presented in the upper panel of Table 57.2, while the classification of the 48 out-sample bonds are presented in the lower panel of Table 57.2. In Table 57.9, summary statistics of the in- and out-sample analysis are given. The in-sample explanatory and discriminant powers of the 5 principle components Y1,…,Y5 are 54.48% and 48.81%, respectively; while the out-sample explanatory and discriminant powers of the 5 principle components Y1,…,Y5 are 46.70% and 58.33%, respectively.

## Table 57.2: Classification using principle component analysis.

| Predicted rating | Aa | A | Baa | Ba | B | Total |
| --- | --- | --- | --- | --- | --- | --- |
| Actual rating    |    |   |     |    |   |       |
| IN-SAMPLE        |    |   |     |    |   |       |
| Aa               | 8  | 5 | 0   | 1  | 0 | 14    |
| A                | 3  | 8 | 3   | 2  | 0 | 16    |
| Baa              | 0  | 2 | 8   | 8  | 2 | 20    |
| Ba               | 0  | 1 | 1   | 8  | 6 | 16    |
| B                | 0  | 1 | 3   | 5  | 9 | 18    |
| Total            | 11 | 17| 15  | 24 | 17| 84    |
| OUT-SAMPLE       |    |   |     |    |   |       |
| Aa               | 2  | 1 | 0   | 0  | 0 | 3     |
| A                | 1  | 6 | 2   | 1  | 0 | 10    |
| Baa              | 0  | 1 | 5   | 6  | 1 | 13    |
| Ba               | 0  | 1 | 3   | 10 | 0 | 14    |
| B                | 0  | 0 | 0   | 3  | 5 | 8     |
| Total            | 3  | 9 | 10  | 20 | 6 | 48    |

## 57.4.2 Credit-scoring model based on Fisher's discriminant analysis

In the predictive model FDA based on Fisher's discriminant analysis, four discriminant functions $D_1 = \xi_1'\Sigma^{-1/2} X, ..., D_4 = \xi_4'\Sigma^{-1/2} X$ are determined. The coefficients $\xi_1'\Sigma^{-1/2}, ..., \xi_4'\Sigma^{-1/2}$ are presented in Table 57.3. From Table 57.3, the first discrimination function $D_1$ is mostly related to the six financial variables: Subordination ($X_1$), Sales/net worth ($X_5$), Sales/total assets ($X_{11}$), Net income/net worth ($X_{12}$). The second discriminant function $D_2$ is mostly related to: price/earnings ($X_8$), Years of consecutive dividend ($X_9$), Issue size ($X_{16}$), Common stock shares number ($X_{17}$), Net income: CV ($X_{19}$), Net income/total assets: mean ($X_{21}$), Net income/total assets: CV ($X_{22}$), Net income and interest/interest: mean ($X_{24}$), Long-term debt/total assets: mean ($X_{25}$), Long-term debt/total assets: CV ($X_{27}$). The third discriminant function $D_3$ is mostly related to the financial variables: Total assets ($X_2$), Net income/sales ($X_6$), Earnings per Share: $X_{15}$, Market value of common stock/long-term debt ($X_{18}$), Sales/total assets: mean ($X_{26}$), Market value of common stock/long-term debt: mean ($X_{31}$). For the fourth discriminant function $D_4$, the related variables are: Net working capital/sale ($X_3$), Net worth/total assets ($X_4$), Long-term debt/total assets ($X_{10}$), Net working capital ($X_{13}$), Sales ($X_{14}$), Total assets: mean ($X_{23}$), Long-term debt/net worth ($X_{34}$).

In Table 57.3, the explanatory powers of the four discriminant functions $D_1, ..., D_4$ are 2.92%, 0.52%, 0.42%, and 0.15%, respectively. Table 57.4 presents the classification of the 84 in-sample and 48 out-sample bonds into one of the 5 ratings B, Ba, Baa, A, Aa using the four discriminant functions $D_1, ..., D_4$. In Table 57.9, the in-sample explanatory and discriminant powers of the four discriminant functions $D_1, ..., D_4$ are 4.01% and 88.10%, respectively; while the out-sample explanatory and discriminant powers are 46.70% and 58.33%, respectively.

## 57.4.3 Credit-scoring model based on stepwise discriminant analysis

For the predictive model SDA based on stepwise discriminant analysis of Pinches and Mingo (1973), 6 out of the 35 financial variables are selected, they are: Subordination ($X_1$), Years of consecutive dividend ($X_9$), Issue size ($X_{16}$), Net income and interest/interest: mean ($X_{24}$), Long-term debt/total assets: mean ($X_{25}$), Net Income/Total Assets ($X_{35}$). The coefficients $\xi_1'\Sigma^{-1/2}, ..., \xi_4'\Sigma^{-1/2}$ for the four discriminant functions

### Table 57.3: Coefficients and explained variances of Fisher's discriminant functions.

| Discriminant function | D₁ | D₂ | D₃ | D₄ |
|---|---|---|---|---|
| Coefficients | Σ^{-1/2}ξ₁ | Σ^{-1/2}ξ₂ | Σ^{-1/2}ξ₃ | Σ^{-1/2}ξ₄ |
| Subordination: X₁ | -2.1657 | 1.3692 | 0.5474 | -0.7433 |
| Total Assets: X₂ | 0.3351 | 0.5962 | -1.4899 | -1.2458 |
| Net Working Capital/Sale: X₃ | 0.3990 | 0.1564 | 0.5201 | -1.5259 |
| Net Worth/Total Assets: X₄ | 0.1178 | 0.2874 | -0.1187 | -1.2046 |
| Sales/Net Worth: X₅ | -1.4326 | -0.7671 | 0.0206 | -0.0619 |
| Net Income/Sales: X₆ | -0.1464 | -0.3684 | -0.3772 | 0.2522 |
| Recent Market High of Debt: X₇ | -0.1795 | -0.2217 | -0.5889 | -0.2171 |
| Price/Earnings: X₈ | 0.5116 | 0.5450 | -0.5287 | -0.0758 |
| Years of Consecutive Dividend: X₉ | 1.2557 | 1.3147 | 0.2997 | -0.1760 |
| Long-Term Debt/Total Assets: X₁₀ | -1.2860 | 0.4237 | 0.2559 | 1.6403 |
| Sales/Total Assets: X₁₁ | 0.6661 | 0.1158 | -0.4611 | 0.5774 |
| Net Income/Net Worth: X₁₂ | 0.9496 | 0.8184 | -0.1251 | 0.0950 |
| Net Working Capital: X₁₃ | -0.1144 | 0.1999 | -0.5364 | 1.3835 |
| Sales: X₁₄ | 0.3962 | -0.2526 | 0.4669 | -2.7178 |
| Earnings per Share: X₁₅ | 0.2654 | -0.2279 | -0.7188 | 0.0062 |
| Issue Size: X₁₆ | -0.4847 | -0.6352 | 0.2832 | -0.0702 |
| Common Stock Share Number: X₁₇ | 0.7332 | -0.9775 | -0.0062 | 0.1613 |
| Market Value of Common Stock/Long-Term Debt: X₁₈ | 0.0610 | 0.3236 | 0.3602 | -0.2327 |
| Net Income: CV: X₁₉ | 0.2343 | 1.3633 | -1.334 | 0.9371 |
| Long-Term Debt/Net Worth: Mean: X₂₀ | -0.2368 | -0.2273 | 0.2314 | -0.0657 |
| Net Income/Total Assets: Mean: X₂₁ | -0.0588 | -0.4655 | 0.1800 | -0.1544 |
| Net Income/Total Assets: CV: X₂₂ | -0.4238 | -1.2433 | 0.6014 | -0.6584 |
| Total Assets: Mean: X₂₃ | -0.0610 | 1.2332 | 1.0264 | 2.2914 |
| Net Income and Interest/Interest: Mean: X₂₄ | -1.0246 | -1.3212 | 0.2087 | -0.3177 |
| Long-Term Debt/Total Assets: Mean: X₂₅ | 0.0057 | -1.0395 | 0.8487 | -0.0427 |
| Sales/Total Assets: Mean: X₂₆ | -0.1709 | -0.1948 | 0.3080 | 0.0962 |
| Long-Term Debt/Total Assets: CV: X₂₇ | 0.6759 | -0.8933 | -0.3744 | 0.5599 |
| Net Income and Interest/Interest: CV: X₂₈ | 0.4779 | 0.3965 | -0.3415 | -0.6677 |
| Market Price Change: CV: X₂₉ | -0.2217 | -0.3004 | 0.4921 | -0.1294 |
| Earnings per Share Change: CV: X₃₀ | 0.0535 | 0.0055 | -0.3456 | 0.0779 |
| Market Value of Common Stock/Long-Term Debt: Mean: X₃₁ | -0.2949 | 0.6048 | 1.2291 | 0.1716 |
| Sales Percentage Change: Mean: X₃₂ | -0.0761 | 0.1408 | 0.2934 | -0.0972 |
| Net Income Percentage Change: Mean: X₃₃ | 0.1746 | 0.0659 | 0.1662 | -0.1869 |
| Long-Term Debt/Net Worth: X₃₄ | 0.6467 | -0.2491 | -0.5588 | -1.2213 |
| Net Income/Total Assets: X₃₅ | -0.1981 | -0.1126 | -0.0408 | -0.0579 |
| Variance | 1.0209 | 0.1824 | 0.1470 | 0.0538 |
| Cumulative percentage of total variance | 2.92% | 0.52% | 0.42% | 0.15% |
