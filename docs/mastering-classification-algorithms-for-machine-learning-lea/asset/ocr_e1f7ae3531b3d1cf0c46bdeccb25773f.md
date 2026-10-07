# Decision Tree Algorithm 133

Let us compute the loss for the threshold $x_1 = 1.00$. So, we split the dataset for $x_1 <= 1.00$, then the dataset on the left-hand side of the split and the dataset on the right-hand side of the split would look as shown in Table 5.2:

| $x_1 \le 1.00$ | | $x_1 > 1.00$ | | |
|---|---|---|---|---||
| x1 | x2 | y | x1 | x2 | y |
| 1 | 4 | 0 | 2 | 4 | 0 |
| 1 | 6 | 0 | 2 | 7 | 1 |
| 1 | 2 | 1 | 5 | 2 | 1 |
| 1 | 7 | 1 | 5 | 4 | 0 |
| | | | 7 | 2 | 1 |
| | | | 7 | 6 | 0 |

**Table 5.2:** The $m_{left}$ and $m_{right}$ dataset at split point $x_i \le 1.00$

From Table 5.2, we get that the number of data points on the left-hand side of the split is four, and thus, $m_{left} = 4$. Similarly, we get that, $m_{right} = 6$. Also, we get that $m = 10$. We must calculate $Gini(left)$ and $Gini(right)$.

To calculate $Gini(left)$, we get the following from Table 5.2.

```
$P(0|left) = 2/4 = 0.5$
P(1|right) = 2/4 = 0.5$
```

So, $Gini(left) = 1 - (0.5^2 + 0.5^2) = 1 - (0.25 + 0.25) = 1 - 0.5 = 0.5$

To calculate $Gini(right)$, we get the following from Table 5.2.

```
$P(0|right) = 3/6 = 0.5$
P(1|right) = 3/6 = 0.5$
```

So, $Gini(right) = 1 - (0.5^2 + 0.5^2) = 1 - (0.25 + 0.25) = 1 - 0.5 = 0.5$

Now, we can calculate the loss at the threshold $x_1 = 1.00$.

```
$J(x_1=1.00) = \frac{\frac{4*0.5+6*0.5}{10}} = \frac{2+3}{10} = \frac{5}{10}=0.5$
```

Let us try one more example to understand the technique. Let us calculate the loss at the threshold $x_2 = 2.50$. So, we split the dataset for $x_2 <= 2.50$, then the dataset on the left-hand side of the split and the dataset on the right-hand side of the split would look as shown in Table 5.3: