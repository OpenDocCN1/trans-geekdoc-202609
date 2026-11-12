# 4 Solving SWAMP with an Integer Linear Program

We introduce a new ILP formulation for solving the decision version of the problem, which asks whether there exists some set \( S \) with density greater than \( \alpha \) for some pre-specified \( \alpha \). More formally, finding \( S \) with \( \Gamma(S) > \alpha \) is equivalent to finding \( S \) for which \( f(S) - \alpha|S| > 0 \). We will solve the latter using an ILP, and once we have the solution, we can solve SWAMP by performing a binary search on \( \alpha \). This construction is similar to the approach by Goldberg [13] for finding the densest subgraph.

We consider the following integer linear program.

```
maximize \(\left( \sum_{e \in E} w(e) \sum_{i=1}^{|e|} \delta_{e,i} \cdot y_{e,i} \right) - \alpha \sum_{v \in V} x_v\)
s.t. \(y_{e,i} \le \frac{1}{i} \sum_{v \in e} x_v\) 	 for \(e \in E, i = 1, 2, \dots, |e|,\) (5)
			\(y_{e,i} \in \{0, 1\}\) 	 for \(e \in E, i = 1, 2, \dots, |e|,\)
			\(x_v \in \{0, 1\}\) 	 for \(v \in V\).
```

In the above, we have defined

```
\(\delta_{e,i} = r_e(i) - r_e(i-1) \ge 0\)
```

so that if we include \( k \) nodes from edge \( e \) in the set \( S \), we know that this gives a reward of

```
\(r_e(k) = \sum_{i=1}^k \delta_{e,i}.\)
```

This ILP includes a variable \( x_v \in \{0, 1\} \) that indicates whether node \( v \) is contained in the optimal density set \( S \) (\( x_v = 1 \)) or not (\( x_v = 0 \)). The variable \( y_{e,i} \) is designed to satisfy

```
\(y_{e,i} = \left\{ \begin{array}{ c l } 1 & \text{if } |e \cap S| \ge i \\ 0 & \text{otherwise.} \end{array} \right.\) (6)
```

Observe that if this is the case, then the first part of the objective function of the ILP is exactly the edge reward

```
\(\sum_{e \in E} w(e) \sum_{i=1}^{|e|} \delta_{e,i} \cdot y_{e,i} = \sum_{e \in E} w(e) \sum_{i=1}^{|e \cap S|} \delta_{e,i} = \sum_{e \in E} w(e) \cdot r_e(|e \cap S|).\)
```

We just need to confirm that for the optimal solution, the \( y_{e,i} \) variables will indeed satisfy Eq. (6). Observe first of all that maximizing the objective, plus the fact that the \( \delta_{e,i} \) are all positive, will ensure that the \( y_{e,i} \) variables will be set to 1 whenever possible. Now, note that the constraint

```
\(y_{e,i} \le \frac{1}{i} \sum_{v \in e} x_v\)
```