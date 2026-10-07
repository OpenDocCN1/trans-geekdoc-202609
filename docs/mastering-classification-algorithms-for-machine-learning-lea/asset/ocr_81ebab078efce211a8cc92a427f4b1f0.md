So, our decision tree looks as shown in Figure Annexure 8.6:

![](bbox=[0.279, 0.137, 0.719, 0.381])

**Figure Annexure 8.6:** Decision Tree after the second split

As we have done before, we will split the dataset, as shown in Table Annexure 8.4, based on the new decision node we created, as shown in Figure Annexure 8.6, that is, based on $x_2 <= 6.5$. Based on this, the dataset on the left-hand side is shown in Table Annexure 8.5, and the dataset on the right-hand side is shown in Table Annexure 8.6:

| x1 | x2 | y |
| 1 | 4 | 0 |
| 7 | 6 | 0 |
| 1 | 6 | 0 |
| 5 | 4 | 0 |
| 2 | 4 | 0 |

**Table Annexure 8.5:** The data points in the dataset (as shown in Table A8.4) where $x_2 \le 6.50$

From Table Annexure 8.5, we see that for all the data points, the value of y is 0. So, we have a leaf node with with the decision y = 0.

| x1 | x2 | y |
| 1 | 7 | 1 |
| 2 | 7 | 1 |

**Table Annexure 8.6:** The data points in the dataset (as shown in Table A8.4) where $x_2 > 6.50$