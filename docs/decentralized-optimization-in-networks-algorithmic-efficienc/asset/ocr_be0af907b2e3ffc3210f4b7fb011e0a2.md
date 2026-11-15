# Algorithm 2 A differentially private decentralized dual averaging algorithm with delays – from the viewpoint of $i \in \mathcal{V}$.

+   1: **Require:** $\alpha_0 > 0, z_{i,1} \in \mathbb{R}^m, x_{i,1} = \Pi_\Omega^h(z_{i,1}, \alpha_0), \text{and } y_{i,1} = e_i \in \mathbb{R}^n$.  
+   2: **Delays:** Every communication link $(j, i)$ belonging to the set $\mathcal{E}$ within the network $\mathcal{G}$ experiences random yet consistently limited communication delays denoted as $\vartheta_{ij}$ for all $j$ that are part of $\mathcal{N}_i^{\text{in}}$.  
+   3: **Set** $k = 1$.  
+   4: **while** $k \le K$ **do**  
+   5: Generate noise $\gamma_{i,k} \sim \mathcal{L}(0, b_k)$.  
+   6: Perturb $z_{i,k}$ by $\gamma_{i,k}$ and obtain $\tilde{z}_{i,k}$ via (5.6).  
+   7: Transmit $A_{ji}y_{i,k}$ and $A_{ji}\tilde{z}_{i,k}$ to node $j \in \mathcal{N}_i^{\text{out}}$; Receive $A_{ij}y_{j,k-\vartheta_{ij}}$ and $A_{ij}\tilde{z}_{j,k-\vartheta_{ij}}$ from node $j \in \mathcal{N}_i^{\text{in}}$.  
+   8: Update $z_{i,k+1}, y_{i,k+1}$ via (5.38); Update $x_{i,k+1}$ via (5.9).  
+   9: **Set** \( k \leftarrow k + 1 \).  
+   10: **Return:** the primal variable \(\{x_{i,k}\}_{k=1}^K\).

# 5.5.2 Main results

The theorem below will demonstrate that Algorithm 2 is capable of not only achieving the anticipated regret, but also guaranteeing $\hat{\epsilon}$-differential privacy in the presence of a communication delay in every connection of the directed networks.

Theorem 5.3. Taking into account the sequence \(\{x_{i,k}\}_{k=1}^K\) produced by Algorithm 2, and based on Assumptions 5.1–5.3, we can deduce the subsequent conclusions:

+   **(a)** Provided that \(\gamma_{i,k}\), where \(i \in \mathcal{V}\), satisfies the conditions stated in Theorem 5.2, Algorithm 2 ensures $\hat{\epsilon}$-differential privacy across \(K\) iterations.  
+   **(b)** Provided that \(\alpha_k\) fulfills the criteria outlined in Theorem 5.2, Algorithm 2 attains a regret of order \(\mathcal{O}(\sqrt{K})\) over the set \(\Omega\).

Proof. It is worth mentioning that Algorithm 2 represents an advancement of Algorithm 1, incorporating the consideration of communication delays. In this context, Theorem 5.3 can be validated through a two-step process, as referenced in [27]. Initially, by employing an expanded directed network, Algorithm 2 (incorporating communication delays) can be converted into an algorithm devoid of delays. Following this transformation, Section 5.4 aids in the assessment of the derived delay-free algorithm’s convergence and privacy-preservation abilities.

Bear in mind that, without delays, our algorithm relies on a communication network denoted as \(\mathcal{G}\) and represented by a row-stochastic matrix \(A\). However, in scenarios involving delays, our intention is to expand \(\mathcal{G}\) into a virtual directed network, denoted as \(\hat{\mathcal{G}}\) and represented by a different row-stochastic matrix \(\hat{A}\). Specifically, we introduce delay nodes (virtual), designated as \(d_{ji}\), along the edge \((i, j)\) of the original network \(\mathcal{G}\). Following this, we construct a delay chain composed of directed edges, namely, \((i, d_1), (d_1, d_2), \dots, (d_{ji}, j)\), and redirect all data from node \(i\) through this chain to reach node \(j\). Furthermore, the cumulative number of delay nodes within the