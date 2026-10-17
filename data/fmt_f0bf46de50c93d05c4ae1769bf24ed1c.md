
3. 对于每个满足 \(0 < y_{i} \leq \alpha\)，\(0 < z_{j} \leq \beta\) 的 \(\langle y_{i}z_{j}\rangle\)，\(\operatorname{T}^{(v_{i}z_{j})}\) 是 \(\mathbb{H}_{\G}^{(v_{i}z_{j})}\) 的一个 `IFT`。

*证明：* 根据定义，“`IFTHG` 的最小 `IFT` `T` 是 \(\mathbb{H}_{\G}\) 的一个横截，满足如下性质：如果 `T1 \subset T`，则 `T1` 不是 \(\mathbb{H}_{\G}\) 的一个 `IFT`”，证明是平凡的。

### 定理 5.4.17
对于一个简单 `IFTHG` \(\mathbb{H}_{\G}\)，有 `T\mathfrak{H}(T\mathfrak{H}(\mathbb{H}_{\G})) = \mathbb{H}_{\G}`。

### 定理 5.4.18
对于任意 `IFTHG` \(\mathbb{H}_{\G}\)，有 `T\mathfrak{H}(T\mathfrak{H}(\mathbb{H}_{\G})) \subseteq \mathbb{H}_{\G}`。

*证明：* 根据定义 5.4.10，存在简单 `IFTHG` \(\mathbb{H}_{\G}\) 的一个部分 `IFTHG` \(\mathbb{H}_{\G}^{'}\)，使得 \(\exists T\mathfrak{H}(\mathbb{H}_{\G}^{'}) = T\mathfrak{H}(\mathbb{H}_{\G})\)。由定理 5.4.17，`T\mathfrak{H}(T\mathfrak{H}(\mathbb{H}_{\G})) = T\mathfrak{H}(T\mathfrak{H}(\mathbb{H}_{\G}^{'}) = \mathbb{H}_{\G}^{'} \subseteq \mathbb{H}_{\G}`。

### 定理 5.4.19
设 \(\mathbb{H}_{\G} = \langle U, \varepsilon, s_1, s_2\rangle\) 是一个 `IFTHG`，且假设

`T \in T\mathfrak{H}(\mathbb{H}_{\G})`。若 \(\mathbb{H}_{\G}^{'} \subseteq supp(T) \subseteq \mathbb{H}_{\G}\)，则 \(\exists\) 一个 `IF` 阈值超边 \(\mathcal{A}\)，其中 \(\langle y_{i}z_{j}\rangle \in \mathcal{A}\) 代表 \(\mathcal{A} \supseteq\) 的隶属度和非隶属度值：

1. \(\langle y_{p}z_{q}\rangle = \underline{h}_{t}(\mathcal{A}) = \underline{h}_{t}\left(T^{(v_{i}z_{j})}\right) > 0\)。

2. \(\mathrm{T}_{\underline{h}_{t}(\mathcal{A})} \cap \mathcal{A}_{\underline{h}_{t}(\mathcal{A})} = \mathbb{H}_{\G}\)。

*证明：* 假设 \(0 < \underline{h}_{t}\left(T^{(v_{i}z_{j})}\right) \leq 1\)，并设 \(\varepsilon^{'}\) 为 `IF` 阈值超边的集合，其中对于每个 \(\tau \in \varepsilon^{'}\)，满足 \(\underline{h}_{t}(\mathcal{A}^{(v_{i}z_{j})}) \geq \underline{h}_{t}\left(T^{(v_{i}z_{j})}\right)\)，且对于所有 \(1 \leq i \leq m\)，\(1 \leq j \leq n\)，有 \(\sum_{u_{i} \in U} \mu_{ij}\left(u_{i}\right) \leq s_{1}\) 和 \(\sum_{u_{i} \in U}\left(1 - \nu_{ij}\left(u_{i}\right)\right) \leq s_{2}\)。

由于 \(\mathrm{T}^{(v_{i}z_{j})}\) 是 \(\mathbb{H}_{\G}^{(v_{i}z_{j})}\) 的一个 `IFT`，且 \(\mathbb{H}_{\G}^{'} \subseteq \mathrm{T}^{(v_{i}z_{j})}\) 非空。此外，对于每个 \(\tau \in \varepsilon^{'}\)，\(\underline{h}_{t}(\tau) \geq \left(T^{(v_{i}z_{j})}\right)\) 成立。另外，假设 \(\mathrm{T}^{(v_{i}z_{j})}\) 是最小 `IFT`，则对于每个 \(\tau \in \varepsilon^{'}\)，\(\underline{h}_{t}(\tau) \geq \left(T^{(v_{i}z_{j})}\right)\)，且存在 \(\mathbb{H}_{\G^{'}t} \neq \mathbb{H}_{\G}\)，使得 \(\mathbb{H}_{\G^{'}t} \in \tau_{\underline{h}_{t}(\tau)} \cap T_{\underline{h}_{t}(\tau)}\)。

定义一个 `IFTHG` \(\mathbb{H}_{\G^{1}} \supseteq\)

$$\begin{array}{c} \mathrm{T}(W)\mathrm{if}\; W\ne\mathbb {H}_{\mathtt{G}}{}^{'}\\ \mathbb {H}_{\mathtt{G}_{1}}(u_{i}) = \left\{ \begin{array}{c} \Lambda(h_{t}(\mathcal{A}')/h_{t}(\mathcal{A})<f_{t}(\mathrm{T}^{(\upsilon_{i},z_{i})}),\; \lor(h_{t}(\mathcal{A}')/h_{t}(\mathcal{A})<f_{t}(\mathrm{T}^{(\upsilon_{i},z_{i})}))\mathrm{if}\; W=\mathbb{H}_{\mathtt{G}}{}^{'} \end{array}\right. \end{array}$$

显然，$\mathbb {H}_{\mathtt{G}_{1}}$ 是 `IFTHG` 的一个 `IFT`，且 $\underline{{h}}_{t}(\mathbb {H}_{\mathtt{G}_{1}}{}^{(\upsilon_{i},z_{i})})<\underline{{h}}_{t}(\mathrm{T}^{(\upsilon_{i},z_{i})})$，这与 `T` 的最小性相矛盾。假设每个 $\tau\in\mathcal{E}^{'}$ 都满足部分 (i) 并且包含 $\mathbb {H}_{\mathtt{G}_{\tau}}{}^{'}\ne\mathbb {H}_{\mathtt{G}}{}^{'}$，其中 $\mathbb {H}_{\mathtt{G}_{\tau}}{}^{'}\in\tau_{\underline{{h}}_{t}(\mathcal{A}')}\cap\mathrm{T}_{\underline{{h}}_{t}(\mathcal{A})}{}^{'}$。该过程被重复，(1) 的论证得出了矛盾，从而完成了证明。

### 定理 5.4.20
设 $\mathbb {H}_{\mathtt{G}}=(U,\mathcal{E},s_{1},s_{2})$ 是一个 `IFTHG`。那么，存在 $\mathrm{T}\in\mathfrak{T}(\mathbb {H}_{\mathtt{G}})$，使得对于 $\mathcal{A}\in\mathcal{E}$，满足 $\mathbb {H}_{\mathtt{G}}{}^{'}\subseteq\mathrm{supp}(\mathrm{T})\subseteq\mathbb {H}_{\mathtt{G}}{}^{'}$，则：

1.  $(\upsilon_{i},z_{i})=\underline{{h}}_{t}(\mathcal{A})$，

2.  对于每个满足 $\underline{{h}}_{t}(\mathcal{A}')>\underline{{h}}_{t}(\mathcal{A})$ 的 $\mathcal{A}'\in\mathcal{E}$，$\underline{{h}}_{t}(\mathcal{A}')$ 的 $(\upsilon_{i},z_{i})$-水平截集不是 $\underline{{h}}_{t}(\mathcal{A})$ 的 $(\upsilon_{i},z_{i})$-水平截集的子超图，并且

3.  $\underline{{h}}_{t}(\mathcal{A})$ 的 $(\upsilon_{i},z_{i})$-水平截集不包含 $\mathbb {H}_{\mathtt{G}}{}_{\underline{{h}}_{t}(\mathcal{A})}$ 的其他任何超边，其中 $(\upsilon_{i},z_{i})$ 表示 $\mathcal{A}$ 的成员度和非成员度值。

*证明：*

*必要性部分：*

1.  设 $\mathrm{T}\in\mathfrak{T}(\mathbb {H}_{\mathtt{G}})$ 且 $0<\underline{{h}}_{t}(\mathrm{T}^{(\upsilon_{i},z_{i})})\leq 1$。那么根据定理 5.4.19，结果 (i) 成立。

2.  假设对于所有满足 (i) 要求条件的 $\mathcal{A}$，存在 $\mathcal{A}'\in\mathcal{E}$ 使得 $\underline{{h}}_{t}(\mathcal{A}')>\underline{{h}}_{t}(\mathcal{A})$ 且 $\mathcal{A}'^{\underline{{h}}_{t}(\mathcal{A})}\subseteq\mathcal{A}^{\underline{{h}}_{t}(\mathcal{A}')}$，则存在 $u\notin\mathbb {H}_{\mathtt{G}}{}^{'}$，使得 $U\in\mathcal{A}'^{\underline{{h}}_{t}(\mathcal{A}')}\cap\mathrm{T}_{\underline{{h}}_{t}(\mathcal{A}')}\subseteq\mathcal{A}^{\underline{{h}}_{t}(\mathcal{A})}\cap\mathrm{T}_{\underline{{h}}_{t}(\mathcal{A})}$，这与定理 5.4.19 相矛盾。

3.  假设对于满足 (1) 和 (2) 的所有 $\mathcal{A}$，存在 $\mathcal{A}'\in\mathcal{E}$，使得 $\emptyset\ne\mathcal{A}'^{\underline{{h}}_{t}(\mathcal{A})}\subset\mathcal{A}^{\underline{{h}}_{t}(\mathcal{A}')}$。由于 $\mathcal{A}'^{\underline{{h}}_{t}(\mathcal{A})}\ne\emptyset$ 且根据 (2)，意味着 $\underline{{h}}_{t}(\mathcal{A}')=\underline{{h}}_{t}(\mathcal{A})=(\upsilon_{i},z_{i})$。

如果 $(\upsilon_{i},z_{i})=\underline{{h}}_{t}(\mathcal{A}')\ \&\ \mathcal{A}'\in\mathcal{E}$ 且 $\emptyset\ne\mathcal{A}''^{\underline{{h}}_{t}(\mathcal{A})}<\mathcal{A}'^{\underline{{h}}_{t}(\mathcal{A})}\subset\mathcal{A}^{\underline{{h}}_{t}(\mathcal{A}')}$，继续该过程，该链必须在无穷多步后终止，因此不妨假设 $(\upsilon_{i},z_{i})<\underline{{h}}_{t}(\mathcal{A})$。但是，存在 $U\nsubseteq\mathbb {H}_{\mathtt{G}}{}^{'}$ 使得 $U\in\mathcal{A}'^{\underline{{h}}_{t}(\mathcal{A})}\cap\mathrm{T}_{\underline{{h}}_{t}(\mathcal{A})}\subseteq\mathcal{A}^{\underline{{h}}_{t}(\mathcal{A})}\cap\mathrm{T}_{\underline{{h}}_{t}(\mathcal{A}')}$，这与定理 5.4.19 相矛盾。

*充分性部分：*

假设 $\mathcal{A}\in\mathcal{E}$ 满足条件 (1) 和 (2)。由 (1) 可知，$\underline{{h}}_{t}(\mathcal{A})=(\upsilon_{i},z_{i})$，其中 $(\upsilon_{i},z_{i})$ 是 $\mathcal{F}(\mathbb {H}_{\mathtt{G}})$ 中的某个成员。由 (2) 和 (3) 可知，对于所有 $\mathcal{A}'\in\mathcal{E}$ 且 $\mathcal{A}'\ne\mathcal{A}\ \&\ \underline{{h}}_{t}(\mathcal{A}')\ge\underline{{h}}_{t}(\mathcal{A})$，存在 $U\in\mathcal{A}'^{\underline{{h}}_{t}(\mathcal{A})}\setminus\mathcal{A}^{\underline{{h}}_{t}(\mathcal{A})}$。设 $V_{\mathcal{A}}$ 为 $\mathbb {H}_{\mathtt{G}}$ 中所有顶点的集合，且 $V_{\mathcal{A}}\cap\mathcal{A}^{\underline{{h}}_{t}(\mathcal{A})}=\emptyset$。

构造初始横截序列 $\tau_{s} \subseteq U$，对于每个 $s, 1 \leq s < i$ 且 $\tau_{s} \subseteq U_{v} \cup U_{f}$。显然，$U_{i} \in \tau_{i} \setminus \backslash$。重复该过程，最终得到一个最小 `IFT`，其值为 $(y_{p} z_{i}) = \underline{h}_{i}(\mathcal{A}) = \underline{h}_{t}(T^{y_{i} z_{i}})$。

### 定理 5.4.21
设 $\mathbb{H}_{\mathbb{G}}=(U, \mathcal{E}; s_{1}, s_{2})$ 是一个 `IFTHG`，其中 $\mathcal{F}(\mathbb{H}_{\mathbb{G}}) = \{y_{1}, y_{2}, \ldots, y_{i}^{*}, z_{1}, z_{2}, \ldots, z_{i}^{*}\}$，使得 $0 \leq y_{i} \leq \underline{h}_{u}(\mathbb{H}_{\mathbb{G}})$ 且 $0 \leq z_{i} \leq \underline{h}_{f}(\mathbb{H}_{\mathbb{G}})$。此外，设 $\mathbb{H}^{(y_{i} z_{i})}$ 为基本 `IFTHG`，满足重复 $\mathcal{A}^{\prime} \Longleftrightarrow \underline{h}_{i}(\mathcal{A}^{\prime}) = (y_{p} z_{i})$ 且 `supp`($\mathcal{A}^{\prime}$) 是 $\mathbb{H}^{(y_{i} z_{i})}$ 的超边。那么 `T\mathfrak{G}(T\mathfrak{G}(\mathbb{H}_{\mathbb{G}}))` 是 $\mathbb{H}_{\mathbb{G}}^{(y_{i} z_{i})}$ 的一个部分 `IFTHG`。
