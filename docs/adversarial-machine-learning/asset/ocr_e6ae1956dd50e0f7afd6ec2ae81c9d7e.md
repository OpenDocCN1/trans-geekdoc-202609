![](bbox=[0.2, 0.125, 0.895, 0.545])

Figure 6.6 The convex hull for a set of queries and the resulting bounding balls for several \(\ell_p\) costs. Each row represents a unique set of positive ("x" points) and negative ("o" points) queries, and each column shows the implied upper bound (the black dashed line) and lower bound (the black solid line) for a different \(\ell_p\) cost. In the first row, the body is defined by a random set of seven queries, in the second, the queries are along the coordinate axes, and in the third, the queries are around a circle.

for \(p \in (1, \infty)\) and is otherwise

```
\| \mathbf{x}^* \|_\infty = \max \left[ \frac{1}{D}, \frac{1}{D}, \dots, \frac{1}{D} \right] \\
= D^{-1}.
```

# ## 8.3.1.1 Bounding \(\ell_p\) Balls

In general, suppose one probes along some set of \(M\) unit directions, and eventually there is at least one negative point supporting an upper bound of \(C_0^-\) and \(M\) positive points supporting a lower bound of \(C_0^+\). However, the lower bound provided by those \(M\) positive points is the cost of the largest \(\ell_p\) cost ball that fits entirely within their convex hull; let's say this cost is \(C^\dagger \le C_0^+\). To achieve \(\epsilon\)-multiplicative optimality, we