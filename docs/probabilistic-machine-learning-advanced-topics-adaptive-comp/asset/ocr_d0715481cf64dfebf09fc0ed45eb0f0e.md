measures \(\hat{p}_n, \hat{\nu}_n\). Using (6.192) to approximate the corresponding (6.196) is doomed to fail, as various results [FG15] have shown in relevant settings (notably for measures in \(\mathbb{R}^q\)) that the sample complexity of the estimator provided by (6.192) to approximate (6.196) is of order \(1/n^{1/q}\). In other words, the gap between \(W_2(\mu, \nu)\) and \(W_2(\hat{\mu}_n, \hat{\nu}_n)\) is large in expectation, and decreases extremely slowly as \(n\) increases in high dimensions. Thus solving (6.196) exactly between these samples is mostly time wasted on overfitting. To address this curse of dimensionality, it is therefore extremely important in practice to approach (6.196) using a more careful strategy, one that involves regularizations that can leverage prior assumptions on \(\mu\) and \(\nu\). While all approaches outlined above using neural networks can be interpreted under this light, we focus in the following on a specific approach that results in a convex problem that is relatively simple to implement, embarrassingly parallel, and with quadratic complexity.

# 6.8.3.6 Obtaining smoothness using entropic regularization

A computational approach to speedup the resolution of (6.192) was proposed in [Cut13], building on earlier contributions [Wil69; KY94] and a filiation to the Schrödinger bridge problem in the special case where \(c=d^2\) [Léo14]. The idea rests upon regularizing the transportation cost by the Kullback-Leibler divergence of the coupling to the product measure of \(\mu, \nu\),

\(W_{c,\gamma}(\mu, \nu) \triangleq \inf_{\pi \in \Pi(\mu, \nu)} \int_{\mathcal{X}^2} d(\mathbf{x}, \mathbf{y})^p d\pi(\mathbf{x}, \mathbf{y}) + \gamma D_{\mathbb{KL}}(\pi \| \mu \otimes \nu).\) (6.213)

When instantiated on discrete measures, this problem is equivalent to the following \(\gamma\)-strongly convex problem on the set of transportation matrices (which should be compared to (6.192))

\(\text{OT}_{C, \gamma}(\mathbf{a}, \mathbf{b}) = \min_{P \in \mathbb{R}_+^{n \times m}, P \mathbf{1}_m = \mathbf{a}, P^T \mathbf{1}_n = \mathbf{b}} \langle P, C \rangle \triangleq \sum_{i,j} P_{ij} C_{ij} - \gamma \mathbb{H}(P) + \gamma (\mathbb{H}(\mathbf{a}) + \mathbb{H}(\mathbf{b})) ,\) (6.214)

which is itself equivalent to the following dual problem (which should be compared to (6.198))

\(\text{OT}_{C, \gamma}(\mathbf{a}, \mathbf{b}) = \max_{\mathbf{f} \in \mathbb{R}^n, \mathbf{g} \in \mathbb{R}^m} \mathbf{f}^T \mathbf{a} + \mathbf{g}^T \mathbf{b} - \gamma (e^{\mathbf{f}/\gamma})^T K e^{\mathbf{g}/\gamma} + \gamma (1 + \mathbb{H}(\mathbf{a}) + \mathbb{H}(\mathbf{b}))\) (6.215)

and \(K \triangleq e^{-C/\gamma}\) is the elementwise exponential of \(-C/\gamma\). This regularization has several benefits. Primal-dual relationships show an explicit link between the (unique) solution \(P^*_\gamma\) and a pair of optimal dual variables \((\mathbf{f}^*, \mathbf{g}^*)\) as

\(P^*_\gamma = \text{diag}(e^{\mathbf{f}/\gamma}) K \text{diag}(e^{\mathbf{g}/\gamma})\) (6.216)

Problem (6.215) can be solved using a fairly simple strategy that has proved very sturdy in practice: a simple block-coordinate ascent (optimizing alternatively the objective in \(\mathbf{f}\) and then \(\mathbf{g}\)), resulting in the famous Sinkhorn algorithm [Sin67], here expressed with log-sum-exp updates, starting from an arbitrary initialization for \(\mathbf{g}\), to carry out these two updates sequentially, until they converge:

\(\mathbf{f} \leftarrow \gamma \log \mathbf{a} - \gamma \log K e^{\mathbf{g}/\gamma} \qquad \mathbf{g} \leftarrow \gamma \log \mathbf{b} - \gamma \log K^T e^{\mathbf{f}/\gamma}\) (6.217)

The convergence of this algorithm has been amply studied (see [CK21] and references therein). Convergence is naturally slower as \(\gamma\) decreases, reflecting the hardness of approaching LP solutions, as studied in [AWR17]. This regularization also has statistical benefits since, as argued in [Gen+19], the sample complexity of the regularized Wasserstein distance improves to a \(O(1/\sqrt{n})\) regime, with, however, a constant in \(1/\gamma^{q/2}\) that deteriorates as dimension grows.