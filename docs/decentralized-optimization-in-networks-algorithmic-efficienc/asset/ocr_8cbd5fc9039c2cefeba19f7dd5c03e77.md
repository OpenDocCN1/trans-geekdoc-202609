# Algorithm 1 The proposed decentralized algorithm (ZO-DDA) at each node $i \in \mathcal{V}$.

+   1: **Initialization:** Each node \(i\) starts with \(\alpha_0 > 0, q_1^i \in \mathbb{R}^m, x_1^i = \Pi_{(1-\xi)\Omega}^\phi(q_1^i, \alpha_0)\), and \(v_1^i = 1\).
+   2: Set \(t = 1\).
+   3: **while** \(t \le T\) **do**
+   4: Calculate subgradient estimator \(\hat{g}_t^i(x_t^i)\) via
+   \[\hat{g}_t^i(x_t^i) = \frac{m}{\delta}(f_t^i(x_t^i + \delta b_t^i) - f_t^i(x_t^i)) b_t^i.\]
+   5: Generate noise \(\vartheta_t^i \sim \mathcal{L}(0, b_t)\).
+   6: Perturb \(q_t^i\) by \(\vartheta_t^i\) and gain \(\tilde{q}_t^i\) via
+   \[\tilde{q}_t^i = q_t^i + \vartheta_t^i.\]
+   7: Transmit \(c_t^{ji} v_t^i\) and \(r_t^{ji} \tilde{q}_t^i\) to its out-neighbors \(j \in \mathcal{N}_{t,\text{out}}^i\).
+   8: Receive \(c_t^{ij} v_t^j\) and \(r_t^{ij} \tilde{q}_t^j\) from its in-neighbors \(j \in \mathcal{N}_{t,\text{in}}^i\).
+   9: Update the auxiliary variable \(v_{t+1}^i\) and the dual variable \(q_{t+1}^i\) via
+   \[v_{t+1}^i = \sum_{j=1}^n c_t^{ij} v_t^j,\]
+   \[q_{t+1}^i = \sum_{j=1}^n r_t^{ij} \tilde{q}_t^j + \frac{\hat{g}_t^i(x_t^i)}{v_{t+1}^i}.\]
+   10: Update the primal variable \(x_{t+1}^i\) via
+   \[x_{t+1}^i = \Pi_{(1-\xi)\Omega}^\phi(q_{t+1}^i, \alpha_t).\]
+   11: Set \(t \leftarrow t + 1\).
+   12: **Return:** the primal variable \(\{x_t^i\}_{t=1}^T\).

[32,34,52]. The primary distinction between these estimators lies in the fact that for smaller values of \(\delta\), the norm bound of one-point estimators surpasses that of two-point estimators, as elaborated in [30]. Consequently, Algorithm 1 prefers the utilization of two-point sampling gradient estimators, anticipating enhanced performance results [30]. Furthermore, Algorithm 1 distinguishes itself from related algorithms in [22,25,27,29,35,40] by offering three compelling advantages: (i) It circumvents the need for direct gradient computation, relying solely on a zeroth-order oracle; (ii) It is adept at accommodating time-varying directed networks through the employment of a rescaled subgradient estimator; (iii) It ensures privacy protection through the implementation of a differentially private strategy.