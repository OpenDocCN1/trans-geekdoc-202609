```
Algorithm 1 A Projected Decentralized Variance-Reduction Algorithm: for node \( i \in \mathcal{V} \).

1: **Initialization:** Set \( x_0^i = \mathbf{0} \in \mathbb{R}^p \), \( s_0^i = P_{\Omega_0}(x_0^i) \), \( t_0^{i,j} = \mathbf{0} \in \mathbb{R}^p \), \( g^i(s_0^i) = \nabla f(s_0^i) \in \mathbb{R}^p \), \( y_0^i = g^i(s_0^i) \in \mathbb{R}^p \), and \( t_0^i = [\nabla f^{i,1}(s_0^i) \dots \nabla f^{i,n^i}(s_0^i)]^\text{T} \), where \( p \) is the dimension of \( x \).
2: for \( k = 1, 2, \dots \) do
3: Update the state \( x_k^i \) via (3.6a).
4: Compute the auxiliary variable \( s_k^i \) via (3.6b).
5: Choose \( \chi_k^i \) uniformly and randomly from \( \{1, \dots, n^i\} \).
6: Compute the local gradient estimator \( g^i(s_k^i) = \nabla f^{i, \chi_k^i}(s_k^i) - \nabla f^{i, \chi_k^i}(t_k^{i, \chi_k^i}) + \frac{1}{n^i} \sum_{j=1}^{n^i} \nabla f^{i,j}(t_k^{i,j}) \).
7: If \( j = \chi_k^i \), then \( t_k^j = s_k^i \), else \( t_k^j = t_k^{i, \chi_k^i} \).
8: Compute the local gradient tracker \( y_k^i \) via (3.6c).
9: **end for**
```

iteration \( k \), while \( \nabla f^{i,j}(t_k^{i,j}) \) signifies the corresponding latest component gradient. At node \( i \), the \( \chi_k^i \)th component gradient, specifically \( \nabla f^{i, \chi_k^i}(t_k^{i, \chi_k^i}) \), is chosen uniformly and at random from this gradient table during each iteration \( k \). Following this selection, the local gradient estimate is then derived by

```
\( g^i(s_k^i) = \nabla f^{i, \chi_k^i}(s_k^i) - \nabla f^{i, \chi_k^i}(t_k^{i, \chi_k^i}) + \frac{1}{n^i} \sum_{j=1}^{n^i} \nabla f^{i,j}(t_k^{i,j}) \).
```

Upon calculating \( g^i(s_k^i) \), all gradient table entries remain unaltered, with the exception of updating the \( \chi_k^i \)th entry to \( \nabla f^{i, \chi_k^i}(s_k^i) \).

> **Remark 3.1.** For large-scale data application scenarios, our work stands out due to its enhanced computational efficiency, an aspect that is noticeably absent in [26]. The problems encountered in our research can be summarized as follows: (i) Achieving a convergence rate comparable to the existing unconstrained algorithm [19] is demanding, primarily because we have incorporated the projection operator to accommodate the closed convex set constraint. (ii) The theoretical analysis of our novel algorithm is more complex than that of an unconstrained optimization algorithm. This complexity arises from the introduction of the variance-reduction technique, which we have employed to elevate computational efficiency.

# 3.4 Convergence analysis

To facilitate analysis, we define \( x_k = [x_k^1, \dots, x_k^m]^\text{T} \in \mathbb{R}^{m \times p} \), \( s_k = [s_k^1, \dots, s_k^m]^\text{T} \in \mathbb{R}^{m \times p} \), \( y_k = [y_k^1, \dots, y_k^m]^\text{T} \in \mathbb{R}^{m \times p} \), \( \nabla F(s_k) = [\nabla f^1(s_k^1), \dots, \nabla f^m(s_k^m)]^\text{T} \in \mathbb{R}^{m \times p} \),