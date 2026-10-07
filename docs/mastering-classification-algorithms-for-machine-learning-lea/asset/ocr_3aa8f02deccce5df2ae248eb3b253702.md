| x1 | x2 | y |
|---|---|--|
| 1 | 2 | 1 |
| 5 | 2 | 1 |
| 7 | 2 | 1 |

Table 5.7: The data points in the dataset (as shown in Table 5.1) where $x_2 \le 3.50$

Let us calculate the Gini index for the dataset, as shown in Table 5.7. Let us call the dataset in Table 5.7 d2. So, we get as follows:

$P(0|d2) = 0/3 = 0$ and $P(1|d2) = 3/3 = 1$

$Gini(d2) = 1 - (+) = 1 - 1 = 0$

From our understanding of the Gini index, we know that the Gini index of 0 means that the dataset is pure and has no impurity. So this dataset need not be split any further.

So, we have one more node for our decision tree. However, this node cannot be split any further. Such nodes are called Leaf Nodes. Leaf Nodes provide a decision. In this example, we get the decision that when $x_i \le 3.5$, the value of y should be 1.

The updated decision tree is shown in Figure 5.5.

![](bbox=[0.327, 0.542, 0.673, 0.765])

Figure 5.5: Updated Decision Tree with a Leaf Node (shown in orange color)

Now, let us consider the dataset on the right-hand side of the root node, as shown in Figure 5.4. In other words, we consider only the data points (as shown in Table 5.1) where $x_2 \ge 3.5$. We have the dataset as shown in Table 5.8: