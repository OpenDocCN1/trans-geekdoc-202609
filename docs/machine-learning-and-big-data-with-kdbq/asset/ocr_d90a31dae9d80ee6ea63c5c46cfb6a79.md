# 480 MACHINE LEARNING

The optimisation of the outcome – the entire decision tree and the corresponding means – not computationally feasible to be achieved in one go. The problem is highly non-linear and data-dependent, which will be exploited in the next chapter when we bag trees. It is thus more convenient to proceed with a greedy algorithm, which does not aim to provide a global minimum. It reaches a satisfactory level for the loss function in a numerically stable manner.

The greedy algorithm for a decision tree is constructed as follows:

+   * Start with root node – the entire data set.
* Set the feature $i$, with $i \in \{1, \dots, N\}$, and the threshold $\xi_i$ to define the binary choice:

```
$domain_1(i, \xi_i) = \{x| |x_i| \le \xi_i\}\quad (24.6)\ndomain_2(i, \xi_i) = \{x| |x_i| > \xi_i\}\quad (24.7)$
```

- The feature index and $\xi_i$ are found in a solution to:

```
$$\min_{i,\xi_i} [ \min_{c_1} \sum_{x_j \in domain_1(i,\xi_i)} (y_j - c_1)^2 + \min_{c_2} \sum_{x_j \in domain_2(i,\xi_i)} (y_j - c_2)^2 ] \quad (24.8)$
```

- The inner minimization is indeed trivial:

```
$c_l = mean(x_j)$ with $x_j \in domain_l(i,\xi_i)$ for $l = 1, 2.\quadquad (24.9)$
```

+   * For a given $i$, the split $\xi_i$ is found by minimising the sum of squares across splits.
* The procedure is iteratively repeated on both domains.
* The algorithm proceeds until the stopping rule is reached.

The stopping rule is thus needed, and it represents a hyperparameter of the model. The first choice is some threshold on the improvement of the loss function itself. This is in line with the greedy approach; when a given step does not provide short-term profit, the algorithm stops. The disadvantage of the approach is that a split which does not improve the overall loss function may well open significant improvements in subsequent splits.

The preferred algorithm follows a slightly different philosophy. First, the decision tree is grown maximally, with the stopping rule being a minimum size of leaf nodes. The fully grown decision tree is then subsequently pruned. The motivation is to build a maximum tree and merge any branches which do not bring significant improvements. The way to perform this operation is called “cost-complexity” pruning.