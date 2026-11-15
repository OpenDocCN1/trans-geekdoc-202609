+   **Algorithm 1** An effective differentially private decentralized dual averaging algorithm – from the viewpoint of \( i \in \mathcal{V} \).
+   1: Require: \( \alpha_0 > 0, z_{i,1} \in \mathbb{R}^m, x_{i,1} = \Pi_\Omega^h(z_{i,1}, \alpha_0) \), and \( y_{i,1} = e_i \in \mathbb{R}^n \).
+   2: Set \( k = 1 \).
+   3: while \( k \le K \) do
+   4: Generate noise \( \gamma_{i,k} \sim \mathcal{L}(0, b_k) \).
+   5: Perturb \( z_{i,k} \) by \( \gamma_{i,k} \) and obtain \( \tilde{z}_{i,k} \) via
+      \( \tilde{z}_{i,k} = z_{i,k} + \gamma_{i,k} \).
+   6: Send \( A_{ji}y_{i,k} \) and \( A_{ji}\tilde{z}_{i,k} \) to node \( j \in \mathcal{N}_i^{\text{out}} \); Receive \( A_{ij}y_{j,k} \) and \( A_{ij}\tilde{z}_{j,k} \) from node \( j \in \mathcal{N}_i^{\text{in}} \)
+   7: Update \( x_{i,k+1}, z_{i,k+1}, \) and \( y_{i,k+1} \) via
+      \( z_{i,k+1} = \sum_{j=1}^n A_{ij}\tilde{z}_{j,k} + \frac{g_{i,k}}{\gamma_{i,k}}, \\)
+      \( y_{i,k+1} = \sum_{j=1}^n A_{ij}y_{j,k}, \\)
+      \( x_{i,k+1} = \Pi_\Omega^h(z_{i,k+1}, \alpha_k) \).
+   8: Set \( k \leftarrow k + 1 \).
+   9: Return: the primal variable \( \{x_{i,k}\}_{k=1}^K \).

# 5.4 Convergence guarantees

In this section, we present the theoretical guarantees of Algorithm 1. Initially, we incorporate previously documented research to ease the examination of convergence. Subsequently, we infer the convergence outcomes of Algorithm 1 by utilizing the relevant findings. Ultimately, we conduct a thorough examination of the differential privacy aspect of Algorithm 1.

# 5.4.1 Auxiliary results

In this subsection, we provide three supporting results linked to the directed network denoted as \( \mathcal{G} \), the projection operator defined as \( \Pi_\Omega^h(\cdot) \), and the conjugate-type function \( \mathcal{H}_\Omega^h(v, \alpha) \) described below.

**Lemma 5.1.** [32] Based on Assumptions 5.1 and 5.2, a sequence of stochastic vectors exists, denoted as \( \pi = [\pi_1, ..., \pi_n]^T \), which fulfills the conditions that

+   a) \( \pi^T A = \pi^T, \pi^T 1_n = 1 \);
+   b) there are \( 0 < \varpi < 1, C > 0 \) and \( \theta > 0 \) satisfying that \( |[A^k]_{ij} - \pi_j| \le C \varpi^k, |y_{ii,k} - \pi_i| \le C \varpi^k, \text{and } \theta^{-1} \le y_{ii,k} \le 1, \forall i, j \in \mathcal{V}, k \ge 1 \).