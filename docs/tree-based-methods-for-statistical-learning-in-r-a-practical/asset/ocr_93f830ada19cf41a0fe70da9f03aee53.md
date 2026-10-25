$L = \begin{matrix} \text{No} & \text{Yes} \\ \text{No} & 0 & 1 \\ \text{Yes} & 8 & 0 \end{matrix}$ ,

where the rows represent the true class and the columns represent the predicted class. For example, we're saying that it is 8 times more costly to misclassify a Yes (employee will leave due to attrition) as a No (employee will not leave due to attrition) than it is to misclassify a No as a Yes. Using this loss matrix, we can compute the altered priors as follows:

\(\tilde{\pi}_{no} \propto (0 + 1) \pi_{no} = 1233/1470 = 0.839\)
\(\tilde{\pi}_{yes} \propto (8 + 0) \pi_{yes} = 8 (237/1470) = 1.290\)

Rescaling so that \(\tilde{\pi}_{no} + \tilde{\pi}_{yes} = 1\) gives \(\tilde{\pi}_{no} = 0.394\) and \(\tilde{\pi}_{yes} = 0.606\). Notice how altering the priors resulted in a tree with different splits and node summaries.

The confusion matrix from each tree applied to the learning sample is shown in Table 2.2. Altering the priors by specifying a higher cost for misclassifying the Yeses increased the number of true negatives (assuming No represents the positive class) from 48 to 233, albeit at the expense of decreasing the number of true negatives from 1212 to 163. Finding the right balance is application-specific and requires a lot of thought and collaboration with subject matter experts.

# TABLE 2.2: Confusion matrix from the trees in Figure 2.6.

| | Observed class | |
| | Default priors | Altered priors |
| | No | Yes | No | Yes |
| Predicted class No | 1212 | 189 | 163 | 4 |
| Yes | 21 | 48 | 1070 | 233 |

The tree structure on the left of Figure 2.6 uses the same calculations we worked through for the Swiss banknote example, so let's walk through some of the calculations for the tree on the right.

In any particular node A, we estimate \(p_{no}(A) \propto \tilde{\pi}_{no} \times N_{no,A}/N_{no}\) and \(p_{yes}(A) \propto \tilde{\pi}_{yes} \times N_{yes,A}/N_{yes}\), which are rescaled to sum to one. For instance, if A is the root node, we have \(p_{no}(A) = \tilde{\pi}_{no} = 0.394\) since \(N_{no,A}/N_{no} = 1233/1233 = 1\). Similarly, \(p_{yes}(A) = 0.606\). We can then calculate the impurity of the root node using the Gini index: