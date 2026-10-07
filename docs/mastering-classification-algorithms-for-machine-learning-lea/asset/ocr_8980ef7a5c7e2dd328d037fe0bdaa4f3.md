# Boosting Algorithm 253

| Decision Points | mLeft | mRight | P(0|Left) | P(1|Left) | P(0|Right) | P(1|Right) | Gini(Left) | Gini(Right) | Loss |
|---|---|---|---|---|---|---|---|---|---||
| 3.50 | 1 | 9 | 0/1 | 1/1 | 1.00000 | 8/9 | 0.88889 | 1/9 | 0.11111 | 0.19753 | 0.17778 |
| 4.00 | 1 | 9 | 0/1 | 1/1 | 1.00000 | 8/9 | 0.88889 | 1/9 | 0.11111 | 0.19753 | 0.17778 |
| 4.50 | 1 | 9 | 0/1 | 1/1 | 1.00000 | 8/9 | 0.88889 | 1/9 | 0.11111 | 0.19753 | 0.17778 |
| 5.00 | 1 | 9 | 0/1 | 1/1 | 1.00000 | 8/9 | 0.88889 | 1/9 | 0.11111 | 0.19753 | 0.17778 |
| 5.50 | 1 | 9 | 0/1 | 1/1 | 1.00000 | 8/9 | 0.88889 | 1/9 | 0.11111 | 0.19753 | 0.17778 |
| 6.00 | 4 | 6 | 3/4 | 0.75000 | 1/4 | 0.25000 | 5/6 | 0.16667 | 0.27778 | 0.31667 |
| 6.50 | 4 | 6 | 4/7 | 0.57143 | 3/4 | 0.25000 | 5/6 | 0.83333 | 1/6 | 0.16667 | 0.27778 | 0.31667 |
| 7.00 | 5 | 9 | 8/9 | 0.88889 | 1/9 | 0.11111 | 0/ | - | - | 1/1 | 1.00000 | 0.19753 | 0.17778 |
| 7.50 | 5 | 9 | 8/9 | 0.88889 | 1/9 | 0.11111 | 0/ | - | 1/1 | 1.00000 | 0.19753 | 0.17778 |

Figure 8.4: Calculations for Decision Stump based on data in Table 8.8

We select x <= 5.50 as the decision point. So, we get the decision stump, as shown in Figure 8.5:

![](bbox=[0.258, 0.315, 0.742, 0.497])

Figure 8.5: Decision Stump for the second tree

Now that we have formed the decision stump, let us make predictions using this decision stump on the data in Table 8.8, as shown in Table 8.10:

| x | y | Weight | y2 |
|---|---|---|--|
| 3 | 1 | 0.1 | 0 |
| 6 | 0 | 0.1 | 1 |
| 6 | 0 | 0.1 | 1 |
| 6 | 0 | 0.1 | 1 |
| 7 | 0 | 0.1 | 1 |
| 7 | 0 | 0.1 | 1 |
| 7 | 0 | 0.1 | 1 |
| 7 | 0 | 0.1 | 1 |
| 8 | 1 | 01 | 1 |

Table 8.10: Predictions using decision stump as shown in Figure 8.4. The predictions are in the column