least valuation. Thus, semantic image segmentation could work even if the object being segmented and isolated consists of the majority of image pixels.

# 6.9.4.1 Submodular maximization

While the cardinality constrained submodular maximization problem is NP complete [Fei98], it was shown in [NWF78; FNW78] that the very simple and efficient greedy algorithm finds an approximate solution guaranteed to be within \(1 - 1/e \approx 0.63\) of the optimal solution. Moreover, the approximation ratio achieved by the simple greedy algorithm is provably the best achievable in polynomial time, assuming \(P \neq NP\) [Fei98]. The greedy algorithm proceeds as follows: Starting with \(X_0 = \emptyset\), we repeat the following greedy step for \(i = 0 \dots (k - 1)\):

```
\(X_{i+1} = X_i \cup (\text{argmax}_{v \in V \\ X_i} f(X_i \cup \{v\}))\) (6.223)
```

What the above approximation result means is that if \(X^* \in \text{argmax}\{f(X) : |X| \le k\}\), and if \(\tilde{X}\) is the result of the greedy procedure, then \(f(\tilde{X}) \ge (1 - 1/e)f(X^*)\).

The \(1 - 1/e\) guarantee is a powerful constant factor approximation result since it holds regardless of the size of the initial set \(V\) and regardless of which polymatroid function \(f\) is being optimized. It is possible to make this algorithm run extremely fast using various acceleration tricks [FNW78; NWF78; Min78].

A minor bit of additional information about a polymatroid function, however, can improve the approximation guarantee. Define the total curvature if the polymatroid function \(f\) as \(\kappa = 1 - \min_{v \in V} f(V - v) / f(v)\) where we assume \(f(v) > 0\) for all \(v\) (if not, we may prune them from the ground set since such elements can never improve a polymatroid function valuation). We thus have \(0 \le \kappa \le 1\), and [CC84] showed that the greedy algorithm gives a guarantee of \(\frac{1}{\kappa}(1 - e^{-\kappa}) \ge 1 - 1/e\). In fact, this is an equality (and we get the same bound) when \(\kappa = 1\), which is the fully curved case. As \(\kappa\) gets smaller, the bound improves, until we reach the \(\kappa = 0\) case and the bound becomes unity. Observe that \(\kappa = 0\) if and only if the function is modular, in which case the greedy algorithm is optimal for the cardinality constrained maximization problem. In some cases, non-submodular functions can be decomposed into components that each might be more amenable to approximation.

We see below that any set function can be written as a difference of submodular functions [NB05; IB12] functions, and sometimes (but not always) a given \(h\) can be composed into a monotone submodular plus a monotone supermodular function, or a BP function [BB18], i.e., \(h = f + g\) where \(f\) is submodular and \(g\) is supermodular. \(g\) has an easily computed quantity called the supermodular curvature \(\kappa^g = 1 - \min_{v \in V} g(v) / g(v | V - v)\) that, together with the submodular curvature, can be used to produce an approximation ratio having the form \(\frac{1}{\kappa}(1 - e^{-\kappa(1 - \kappa^g)})\) for greedy maximization of \(h\).

# 6.9.4.2 Discrete constraints

There are many other types of constraints one might desire besides a cardinality limitation. The next simplest constraint allows each element \(v\) to have a non-negative cost, say \(m(v) \in \mathbb{R}_+\). In fact, this means that the costs are modular, i.e., the cost of any set \(X\) is \(m(X) = \sum_{v \in X} m(v)\). A submodular maximization problem subject to a *knapsack constraint* then takes the form \(\max_{X \subseteq V: m(X) \le b} f(X)\) where \(b\) is a non-negative budget. While the greedy algorithm does not solve this problem directly, a