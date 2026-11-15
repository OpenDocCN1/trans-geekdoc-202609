

$$\le n\mathbb{E}[||\sum_{i=1}^n \|y_{i,k}\|^2 + 2\sum_{i=1}^n \langle y_{i,k}, \frac{g_{i,k}}{y_{i,k}} \rangle + \sum_{i=1}^n \|\frac{g_{i,k}}{y_{i,k}}\|^2 ||]$$

$$\le 2n^2 m b_{\max}^2 + n^2 \theta^2 L^2 + 2n \theta L \sqrt{2m} b_{\max} = M_2.$$ (5.27)

由于 $\alpha_k = \alpha_0 / \sqrt{k+1}$，可得 $(1/\alpha_k) < 2\sqrt{K}/\alpha_0$ 且 $\sum_{k=1}^K \alpha_{k-1} \le \sum_{k=1}^K (\alpha_0 / \sqrt{k}) \le 2\alpha_0 \sqrt{K}$。因此，基于公式 (5.19) 和 (5.25)-(5.27)，我们可以得出

$$\phi_1 \le (M_2 \alpha_0 + \frac{2h(x^*)}{\alpha_0}) \sqrt{K} + M_3,$$ (5.28)

其中

$$M_3 = M_1 + \mathcal{H}_{\Omega}^h(-\bar{z}_1, \alpha_0) + \langle \bar{z}_1, x^* \rangle.$$

或者，我们转而考察 $\phi_2$。基于假设 5.2，由此可得

$$\mathbb{E}[\sum_{k=1}^K \sum_{i=1}^n (f_{i,k}(x_{j,k}) - f_{i,k}(x_{i,k})) + \langle g_{i,k}, x_{i,k} - \bar{x}_k \rangle]$$

$$\le \mathbb{E}[\sum_{k=1}^K \sum_{i=1}^n L \|x_{j,k} - x_{i,k}\| + L \|x_{i,k} - \bar{x}_k\|]$$

$$\le \mathbb{E}[\sum_{k=1}^K 3nL \max_{i \in \mathcal{V}} \|x_{i,k} - \bar{x}_k\|].$$ (5.29)

根据引理 5.3，可得

$$\mathbb{E}[\sum_{k=1}^K 3nL \max_{i \in \mathcal{V}} \|x_{i,k} - \bar{x}_k\|]$$

$$= 3nL \mathbb{E}[\sum_{k=1}^K \max_{i \in \mathcal{V}} \|\Pi_{\Omega}^h(z_{i,k}, \alpha_{k-1}) - \Pi_{\Omega}^h(\bar{z}_k, \alpha_{k-1})\|]$$

$$\le 3nL \mathbb{E}[\sum_{k=1}^K \alpha_{k-1} \max_{i \in \mathcal{V}} \|z_{i,k} - \bar{z}_k\|]$$

$$= 3nL \sum_{k=1}^K \alpha_{k-1} \mathbb{E}[\max_{i \in \mathcal{V}} \|z_{i,k} - \bar{z}_k\|].$$ (5.30)

因此，根据 (5.30) 和引理 5.2，我们可以得到

$$\phi_2 \le 3nL \sum_{k=1}^K \alpha_{k-1} \zeta_k \le M_4 \sum_{k=1}^K \alpha_{k-1} \le 2M_4 \alpha_0 \sqrt{K},$$ (5.31)

其中

$$M_4 = 3nL\big(\frac{nC\theta L + \sqrt{2m}b_{\max}}{1 - \varpi} + C \sum_{i=1}^n ||z_{i,1}|| + 2\theta L\big).$$

根据 (5.28) 和 (5.31)，可得

$$\bar{R}_{j,K} \le \phi_1 + \phi_2 \le (M_2\alpha_0 + \frac{2h(x^*)}{\alpha_0} + 2M_4\alpha_0)\sqrt{K} + M_3,$$

从而完成证明。

### Remark 5.5.
根据定理 5.1，显而易见的是，算法 1 能够以次线性速率 $\mathcal{O}(\sqrt{K})$ 实现预期遗憾。这意味着，随着时间范围 $K$ 的增加，每个节点都将逐步使其预期遗憾趋近于零，表明 $\lim_{K\to\infty} \bar{R}_{j,K}/K$ 趋近于 0。此外，定理 5.1 还暗示，$b_{\max}$ 的大小对算法 1 实现的优化精度有直接影响，前提是系统参数不变。具体来说，随着 $b_{\max}$ 上升（在固定灵敏度下表示较低的隐私水平 $\epsilon_k$，如将在随后小节中详细阐述），在系统参数不变的情况下，算法的优化精度会下降。

### Remark 5.6.
似乎，参考文献 [45,55] 中提到的零和相关扰动方法有可能被集成到算法 1 中，以替代差分隐私方法，从而在保持隐私的同时提高算法效率。然而，这种集成并不简单。算法 1 在有向网络中运行，并使用行随机矩阵，这使得在零和相关扰动方案中引入噪声变得复杂，因为这些噪声本质上必须满足网络的噪声平衡。此外，参考文献 [45,55] 中提出的隐私保护分析依赖于关于网络拓扑的更强假设，这使其相比后续小节中详细说明的差分隐私分析，鲁棒性较差。

## 5.4.3 差分隐私分析

在本小节中，我们的主要目标是证明算法 1 可以实现 $\epsilon$-差分隐私。设想一个场景，某些敌对节点正在主动监控节点间交换的敏感数据，并故意试图推断其隐私。差分隐私的核心目标是隐藏节点的敏感信息，从而使敌对节点无法辨别真实的节点数据。此外，根据定义 5.3，灵敏度通过评估单个节点数据在算法 1 数据集中的影响来衡量引入的噪声量。因此，为了确保 $\epsilon$-差分隐私，我们通过限制所提算法的灵敏度来估计所需的噪声水平。

### Lemma 5.5.
基于假设 5.1 和 5.2，$\Delta_k$ 有界，即

$$\Delta_k \le 2L\theta\sqrt{m},$$

其中 $\theta$ 源自引理 5.1，$m$ 表示集合 $\mathcal{V}$ 中每个 $i$ 所属的变量 $z_i$ 的维度。

证明。根据定义 5.3，存在两个相邻数据集，具体为 $U = \bigcup_{k=1}^K U_k$ 和 $U' = \bigcup_{k=1}^K U'_k$，其中 $U_k$ 有能力塑造和定义集合 $\mathcal{V}$ 中所有 $i$ 的每个局部损失函数 $f_{i,k}$。在任何给定时间 $k$，$U_k$ 和 $U'_k$ 可以被视为算法 $\mathcal{B}$ 的输入。因此，$z'_{i,k}$ 和 $z_{i,k}$ 可以分别被视为执行 $\mathcal{B}(U')$ 和 $\mathcal{B}(U)$ 的输出。需要注意的是，当节点间交换的信息被敌对节点截获时，该信息保持不变，即 $\tilde{z}_{i,k}$ 等于 $\tilde{z}'_{i,k}$。因此，结合公式 (5.7)，我们可以推断出以下结论：

$$||z_{i,k+1} - z'_{i,k+1}||_1 \le || \frac{g_{i,k}}{y_{i,i,k}} ||_1 + || \frac{g'_{i,k}}{y_{i,i,k}} ||_1$$

$$\le \theta\sqrt{m} (||g_{i,k}|| + ||g'_{i,k}||)$$

$$\le 2L\theta\sqrt{m},$$ (5.32)

其中第一个不等式利用了 1-范数的性质。基于相邻数据集 $U_k$ 和 $U'_k$ 的灵活特性，定义 5.3 意味着

$$\Delta_k = \sup_{U_k, U'_k: Adj(U_k, U'_k)} ||\mathcal{B}(U_k) - \mathcal{B}(U'_k)||_1 \le 2L\theta\sqrt{m},$$

从而得到所需结果。

引理 5.5 主要表明，算法 1 的灵敏度受变量 $z_{i,k}, y_{i,i,k}$ 的维度 $m$ 以及参数 $L$ 的影响。下面提出的定理确立了算法 1 确保 $\epsilon$-差分隐私。

### Theorem 5.2.
请记住，对于集合 $\mathcal{V}$ 中所有 $i$ 以及从 1 到 $K$ 的 $k$，$\gamma_{i,k}$ 属于 $\mathbb{R}^m$，如公式 (5.6) 所示。该方程还涉及相关参数 $b_k$，定义为 $\Delta_k/\epsilon_k$，其中 $\epsilon_k$ 为正值。给定假设 5.1 和 5.2 中陈述的条件，算法 1 确保 $\epsilon_k$-差分隐私。此外，算法 1 在整个 $K$ 的时间跨度内保持 $\hat{\epsilon}$-差分隐私，其中 $\hat{\epsilon} = \sum_{k=1}^K (\Delta_k / b_k)$。

证明。引入符号 $z_k$ 作为向量 $[z_{1,k}, ..., z_{n,k}]$ 的转置，该向量属于 $\mathbb{R}^{nm}$；同样，令 $z'_k$ 表示 $[z'_{1,k}, ..., z'_{n,k}]$ 的转置，其也位于 $\mathbb{R}^{nm}$。根据定义 5.3，我们可以推断

$$||z_k - z'_k||_1 \le \Delta_k.$$ (5.33)

观察到 $z_k$ 和 $z'_k$ 都属于空间 $\mathbb{R}^{nm}$，并调用 1-范数的特性，我们可以推断

$$\sum_{i=1}^n \sum_{t=1}^m |z_{i,k}(t) - z'_{i,k}(t)| = ||z_k - z'_k||_1 \le \Delta_k,$$

其中 $z'_{i,k}(t)$ 和 $z_{i,k}(t)$ 分别表示 $z'_{i,k}$ 和 $z_{i,k}$ 的第 $t$ 个元素。值得注意的是，在执行 $\mathcal{B}(U'_k)$ 和 $\mathcal{B}(U_k)$ 时，恶意节点的观测是相同的，即 $\tilde{z}_{i,k}$ 等于 $\tilde{z}'_{i,k}$。随后，与参考文献 [23] 中提议 1 的推理一致，只需证明

$$\prod_{i=1}^n \prod_{t=1}^m \frac{[\tilde{z}_{i,k}(t) - z_{i,k}(t)]}{[\tilde{z}'_{i,k}(t) - z'_{i,k}(t)]}$$

$$\le \exp(\frac{||z'_{i,k} - z_{i,k}||_1}{b_k}) \le \exp(\frac{\Delta_k}{b_k}) = e^{\epsilon_k}.$$

此外，可以推断

$$\mathbb{P}[\mathcal{B}(U) \in S] = \prod_{k=1}^K \mathbb{P}[\mathcal{B}(U_k) \in S].$$

因此，可以得出结论

$$\prod_{k=1}^K \mathbb{P}[\mathcal{B}(U_k) \in S] \le \prod_{k=1}^K \exp(\frac{\Delta_k}{b_k}) \cdot \mathbb{P}[\mathcal{B}(U'_k) \in S],$$

根据 $\hat{\epsilon} = \sum_{k=1}^K (\Delta_k / b_k)$，这表明

$$\mathbb{P}[\mathcal{B}(U) \in S] \le \exp(\hat{\epsilon}) \cdot \mathbb{P}[\mathcal{B}(U') \in S].$$

基于定义 5.2，定理 5.2 得出。

根据定理 5.2，显而易见的是，参数 $b_k$ 和灵敏度 $\Delta_k$ 都在确定差分隐私程度方面发挥作用。具体来说，$\Delta_k$ 与隐私水平呈正相关，而 $b_k$ 在任何给定时间 $k$ 与隐私呈负相关。值得注意的是，调整灵敏度 $\Delta_k$ 面临挑战，主要是因为它仅受向量 $z_{i,k}$ 和 $y_{ii,k}$ 的维度 $m$ 以及 Lipschitz 参数 $L$ 的影响。因此，必须仔细考虑选择参数 $b_k$，以确保实现我们所需的 $\epsilon_k$-差分隐私。此外，定理 5.2 澄清了，累积参数 $\hat{\epsilon}$ 代表了 $K$ 次迭代中各个 $\epsilon_k$ 值的总和。这意味着，随着迭代的进展，隐私水平逐渐降低。直观地，在 $K$ 次迭代后相比于任何特定时间 $k$ 的单次迭代，披露更多敏感信息变得不可避免，从而增加了潜在隐私泄露的风险。

