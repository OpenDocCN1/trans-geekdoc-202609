pruning works and how the sequence of $\alpha$ values is computed. For clarity, the number of observations in each class is displayed within each node, and the node numbers appear at the top of each node. For example, node 8 contains 4208 edible mushrooms and 24 poisonous ones. The assigned classification, or majority class, is printed above the class frequencies in each node. This tree was also built using the observed class priors and equal misclassification costs; hence, $R(T)$ is just the proportion of misclassifications in the learning sample: 24/8124 $\approx$ 0.003.

Let $A_i, i \in \{1, 2, 3, 4, 5, 8, 9\}$ denote the seven nodes of the tree in Figure 2.16; in **rpart**, the left and right child nodes for any node numbered $x$ are always numbered $2x$ and $2x+1$, respectively (the root node always corresponds to $x=1$). We can compute the risk of any terminal node using $R(A_i) = N_{j,A}/N_A$. For example, nodes $A_5-A_7$ all have a risk of zero (since they are pure nodes).

![](bbox=[0.15, 0.36, 0.85, 0.65])

FIGURE 2.16: Classification tree with three splits for the mushroom edibility data. The overall risk of the tree is 24/8124 $\approx$ 0.003.

To find $\alpha_1$, we need to first compute $\alpha$ for each of the $|\mathcal{T}_0| - 1 = 3$ internal nodes of the tree, and find which one is the smallest; use the tree diagram in Figure 2.16 to follow along. The $\alpha$ values for the three internal nodes are computed as follows:

```
\alpha_{A_1} = (3916/8124 - 24/8124) / (4 - 1) \approx 0.160
\alpha_{A_2} = (120/8124 - 24/8124) / (3 - 1) \approx 0.006 .
\alpha_{A_4} = (48/8124 - 24/8124) / (2 - 1) \approx 0.003
```