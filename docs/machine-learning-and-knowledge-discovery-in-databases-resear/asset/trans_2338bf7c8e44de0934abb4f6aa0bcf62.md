

```
Input: Stream \(\tau\) of temporal edges, time-duration \(\delta\), predictor \(\mathcal{Q}(\cdot)\), sampling probability \(p \in [0, 1]\).
Output: Estimates \(c_i\) of \(|\mathcal{T}_i|\) for \(i \in [8]\).
1 \(H \leftarrow \emptyset; S_L \leftarrow \emptyset\);
2 \(c_{i, 0} \leftarrow 0; c_{i, 1} \leftarrow 0; c_{i, 2} \leftarrow 0\) for \(i \in [8]\);
3 foreach \(e = (u, v, t) \in \tau\) do
  4 \(H \leftarrow \text{CleanUp}(H, t - \delta); S_L \leftarrow \text{CleanUp}(S_L, t - \delta)\);
  5 \(\forall_{H, H}, \forall_{H, S_L}, \forall_{S_L, S_L} \leftarrow \text{CollectWedges}(H, S_L, e)\);
  6 \(c_{i, 0} \leftarrow \text{UpdateCounts}(c_{i, 0}, \forall_{S_L, S_L}, e)\) for \(i \in [8]\);
  7 \(c_{i, 1} \leftarrow \text{UpdateCounts}(c_{i, 1}, \forall_{H, S_L}, e)\) for \(i \in [8]\);
  8 \(c_{i, 2} \leftarrow \text{UpdateCounts}(c_{i, 2}, \forall_{H, H}, e)\) for \(i \in [8]\);
  9 if \(\mathcal{Q}(e) = 1\) then \(H \leftarrow H \cup \{e\}\);
  10 else if \(\text{BiasedCoin}(p) = true\) then \(S_L \leftarrow S_L \cup \{e\}\);
11 return \(c_i = \frac{c_{i, 0}}{p^2} + \frac{c_{i, 1}}{p} + c_{i, 2}\) for \(i \in [8]\);
```

used to obtain strong guarantees on small memory usage and high estimation accuracy. More in detail, STEP works as follows. First, it initializes two sets, \(H\) and \(S_L\), for storing heavy and (sampled) light edges, respectively (line 1). It then initializes counters \(c_{i,j}\) for each triangle type \(T_i, i \in [8], j \in [0, 2]\) (line 2). All counters are used to output the unbiased estimates \(c_i\) for \(|\mathcal{T}_i|\). STEP then processes the stream \(\tau\) (line 3), and for each edge \(e = (u, v, t)\): 1) it removes edges from \(H\) and \(S_L\) with timestamps smaller than \(t - \delta\) using the CleanUp procedure (line 4). The CleanUp procedure simply updates the sets \(H\) and \(S_L\) by retaining only edges \(e' = (u', v', t')\) with \(t'\) within \(\delta\) time from the timestamp of the current edge \(e\), that is, \(t - t' \le \delta\). 2) it collects all wedges in the sample \( H \cup S_L \),^3 3) all collected wedges are partitioned into three subsets (line 5): \(\forall_{H, H}\) (wedges with both edges in \(H\)), \(\forall_{S_L, S_L}\) (both edges in \(S_L\)), and \(\forall_{H, S_L}\) (one edge in \(H\), the other in \(S_L\)); 4) the counters \(c_{i,j}\) are updated using the UpdateCounts procedure (lines 6-8), tracking occurrences of triangles \(T_i\) with 0, 1, or 2 heavy edges. STEP then calls the predictor \(\mathcal{Q}(e)\) to determine whether \(e\) is heavy or light: if \(\mathcal{Q}(e) = 1\), \(e\) is added to \(H\) (line 9); otherwise, \(e\) is added to \(S_L\) with probability \(p\) (line 10). Finally, STEP outputs estimates \(c_i\) for \(i \in [8]\) by combining and weighting the counters \(c_{i,j}, j = 0, 1, 2\) (line 11).

^3 A wedge is a pair of distinct edges sharing a vertex.

## 3.3 Analysis

Time Complexity. First, we briefly consider the expected time complexity of STEP. Given the input to Algorithm 1, the expected time complexity of STEP is \(\mathcal{O}(m(p m_\delta + |H|)^2)\), where: \(m_\delta\) is the maximum number of edges over \(\tau\) that occur in any time-duration of length \(\delta\), and \(|H|\) is the number of heavy edges in \(H\) during the execution of the algorithm (see our extended version [40]). When \(|H| = o(m_\delta)\) and \(p \ll 1\) (e.g., as in our experiments), STEP is much more efficient than previous approaches (see Sect. 5). That is, STEP scales to large datasets, where previous approaches become impractical (see results in Sect. 4).

**Unbiasedness.** We prove that STEP computes _unbiased estimates_ \(c_i\) of the counts \(|\mathcal{T}_i|\), for \(i \in [8]\), independently of the quality of the predictions of \(\mathcal{Q}(\cdot)\).

**Lemma 1.** Given a stream \(\tau\) of a temporal graph \(G = (V, E)\), a time-duration \(\delta\), and a predictor \(\mathcal{Q}(\cdot)\), each estimate \(c_i, i \in [8]\) reported by **STEP** is an _unbiased estimate_ of the count \(|\mathcal{T}_i|\), that is \(\mathbb{E}[c_i] = |\mathcal{T}_i|\).

**Embedding Predictions.** We now analyze the impact of the predictor \(\mathcal{Q}(\cdot)\) for our algorithm STEP. We first propose a practical model for a predictor, formalizing a _ranking predictor_. Our model is motivated by the fact that most machine learning models are highly optimized for ranking metrics, e.g., Kendall's tau or Spearman's correlation [11, 43]. More in detail, a ranking predictor ranks edges \(e \in \tau\) according to their importance for counts \(|\mathcal{T}_i|\). We show analytically that both a _perfect ranking predictor_ and a _noisy_ one yield accurate estimates and _sublinear space complexity_ for STEP.

*Perfect predictor.* Let \(\omega(e, \mathcal{T}_i) = |\{\Delta : e \in \Delta, \Delta \in \mathcal{T}_i\}|\) be the number of triangles in \(\mathcal{T}_i, i \in [8]\) containing edge \(e \in E\), and \(W(e) = \sum_{i \in [8]} \omega(e, \mathcal{T}_i)\) be the total edge weight of \(e\). Let \(\mathbf{W} \doteq \langle e_1^W, ..., e_m^W \rangle\) be the edges in \(E\) ordered by _non-increasing_ values of their weights \(W(e)\), ties broken arbitrarily. Given two distinct edges \(e, e' \in E\), we use \(e \prec e'\) to denote that \(e\) comes before \(e'\) in the ordering \(\mathbf{W}\). With a slight abuse of notation, we denote with \(e_{\prec j}\) the edge in the \(j\)-th position in \(\mathbf{W}\), and with \(\mathbf{W}(e, \prec)\) the position of edge \(e \in E\) in \(\mathbf{W}\).

(**RANKING PREDICTOR**) Given an integer value \(K > 0\), a _ranking predictor_ \(\mathcal{Q}(\cdot)_K\) is such that \(\mathcal{Q}(e)_K = 1\) iff \(\mathbf{W}(e, \prec) \le K\).

A ranking predictor requires as unique input a parameter \(K\), i.e., the number of edges to classify as heavy. Clearly, \(K\) corresponds to the maximum number of edges to be retained deterministically by STEP.\(^4\) A ranking predictor does not require the knowledge of a threshold over edge weights \(W(e), e \in E\) to classify heavy edges, in contrast with previous literature [7]. That is our predictor model is required to output the ranking \(\mathbf{W}\) without having explicit access to the weights \(W(e), e \in E\), as this would not be practical.

We next introduce a more practical _noisy_ ranking predictor.

*Noisy predictor.* Given two parameters \(\alpha\) and \(K\), we let \(\Pi(\{1, ..., m\})_{(\alpha, K)}\) be the set of permutations of \(m\) elements where three blocks of elements are fixed, i.e., blocks \([1, ..., K - \alpha - 1]\), \([K - \alpha, ..., K + \alpha]\) and \([K + \alpha + 1, ..., m]\). That is, elements from one block can only be permuted inside the same block.

(**NOISY RANKING PREDICTOR**) Given a parameter \(K > 0\) and \(0 \le \alpha \le \min\{m - K + 1, K - 1\}\), an \(\alpha\)_-noisy_ \(K\)_-ranking predictor_ outputs \(\mathbf{W}_\pi = \langle e_{\pi_1}^W, ..., e_{\pi_{|E|}}^W \rangle\), that is the vector \(\mathbf{W}\) permuted according to \(\pi \sim \mathfrak{U}(\Pi(\{1, ..., m\})_{(\alpha, K)})\), where \(\mathfrak{U}(\cdot)\) denotes the uniform distribution over the elements of a set.

Therefore an \(\alpha\)-noisy \(K\)-ranking predictor is such that it correctly classifies the top-(\(K-\alpha-1\)) edges in \(\mathbf{W}\), and the edges with small weight \(W(e)\) (i.e., all edges in position \(j \ge K+\alpha+1\)). While, a noisy ranking predictor can be arbitrarily wrong in classifying edges in position \(K-\alpha, \dots, K+\alpha\) over \(\mathbf{W}\). Where, \(\alpha\) is a *noise parameter*: a larger value for \(\alpha\) corresponds to a less accurate ranking predictor. Our noisy predictor definition closely reflects machine learning models or recommenders with high recall. Note that a 0-noisy predictor corresponds to a ranking predictor (without noise). Let \(\nabla = \max_{i \in [1,m-1]}\{W(e_{\prec i})-W(e_{\prec i+1})\}\) be the maximum difference of the weights for two adjacent edges in the vector \(\mathbf{W}\). Finally let \(\nabla_a = \nabla \cdot (a+1), a \ge 0\).

We now show that STEP computes a relative \(\varepsilon\)-approximation of all the temporal triangle counts \(|T_i|, i \in [8]\) with controlled error probability and sublinear memory usage in \(m_\delta\). We consider both perfect and noisy predictors.\(^5\)

## Theorem 1.

Consider an execution of STEP, with \(\varepsilon > 0\) and \(K = o(m_\delta)\). There exist constants \(C > 1, \gamma \in (0, \frac{1}{2})\) such that:

- 1. when \(\mathcal{Q}(\cdot)_K\) is a ranking predictor then if \(p \ge \frac{C\sqrt{m_\delta}}{\varepsilon|T_i|^{1/2-\gamma}}\), STEP uses \(\mathcal{O}(\varepsilon^{-1}m_\delta^{3/2}/|T_i|^{1/2-\gamma})\) memory in expectation;
- 2. when \(\mathcal{Q}(\cdot)_K\) is an \(\alpha\)-noisy \(K\)-ranking predictor for \(\alpha \ge 1\) then if \(p \ge \frac{C\sqrt{\nabla_a m_\delta}}{\varepsilon|T_i|^{1/2-\gamma}}\), STEP uses \(\mathcal{O}\left(\varepsilon^{-1}m_\delta^{3/2}\sqrt{\nabla_\alpha}/|T_i|^{1/2-\gamma}\right)\) memory in expectation.

In both cases, STEP is a one-pass streaming algorithm with \(\mathbb{P}[\exists i \in [8] : |c_i - |T_i|| \ge \varepsilon|T_i|] \le 1/3\) using sublinear memory.

Consider case 1. and the following event E = "count \(|T_i|^{1/2-\gamma}\) is sufficiently large, for each \(i \in [8]\)." Then Thm. 1 indicates that the sampling probability \(p\) can be set to a sufficiently small value, as \(\sqrt{m_\delta}/|T_i|^{1/2-\gamma} \ll 1\) under E. Consequently, the expected memory usage of STEP becomes sublinear in \(m_\delta\), aligning with established results in concentration theory [5]. Clearly, if E does not hold, then counts \(|T_i|\) are small enough to be obtained with high accuracy using the set \(H\) identified through \(\mathcal{Q}(\cdot)\). Now, consider case 2. from Thm. 1, under E, a noisy predictor increases STEP's expected memory usage by a factor \(\sqrt{\nabla_\alpha}\) (compared to case 1.). That is STEP may miss some triangle counts due to noisy predictions, requiring a larger value for \(p\) to achieve the accuracy guarantees. Nonetheless, if the predictor effectively ranks important (heavy) edges (i.e., \(\sqrt{\nabla_\alpha}\) is not too large), then STEP achieves accurate estimates with reduced variance compared to classical algorithms while maintaining an expected sublinear memory usage. In our extended version [40] we show, as a corollary of Thm. 1 case 1., that if the first \(K\) edges in \(\mathbf{W}\) capture a sufficient number of triangles then Var[\(c_i\)] is a factor \(\mathcal{O}(|T_i|)\) smaller compared to when STEP does not use a predictor.

