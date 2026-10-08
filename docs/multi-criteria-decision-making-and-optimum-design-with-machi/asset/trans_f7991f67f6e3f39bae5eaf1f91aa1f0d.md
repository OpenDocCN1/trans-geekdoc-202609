

# 204 基于机器学习的多准则决策

我们使用 Python 编程通过 SNS 来表示不确定 MCDM 问题，并分析一个现实世界的决策问题。

## 15.2 基本概念

### 15.2.1 球形中性理论集 (SPHERICAL NEUTROSPHIC SET)

首先，在 $\mathbb{X}$ 上计算为 $A = \{(A_r(p), A_i(p), A_f(p)) : p \in X\}$ 的 SNS 满足以下属性：

- (i) $A_r(p), A_i(p), A_f(p) \in [0,1]$
- (ii) $0 \leq A_r(p) + A_i(p) + A_f(p) \leq 1$
- (iii) $0 \leq A_r(p)^2 + A_i(p)^2 + A_f(p)^2 \leq 1$，对于所有 $p \in \mathbb{X}$

$\mathbb{X}$ 上的 SNS 族记为 $SPH_N_S(\mathbb{X})$。

### 15.2.2 SNS 的运算

设 $\mathcal{M}$ 和 $\mathcal{L}$ 是 $\mathbb{X}$ 上任意两个 $SPH_N_S$。那么

- (i) $\mathcal{M}^c = \{\mathcal{M}(p), 1-\mathcal{M}(p), \mathcal{M}(p) : p \in \mathbb{X}\}$ 是 $\mathcal{M}$ 的补集
- (ii) $\mathcal{M}\Pi\mathcal{L} = \{\langle\mathcal{M}(p) \wedge \mathcal{L}(p), \mathcal{M}(p) \wedge \mathcal{L}(p), \mathcal{M}(p) \vee \mathcal{L}(p)\rangle\}$
- (iii) $\mathcal{M}\Pi\mathcal{L} = \{\langle\mathcal{M}(p) \vee \mathcal{L}(p), \mathcal{M}(p) \vee \mathcal{L}(p), \mathcal{M}(p) \wedge \mathcal{L}(p)\rangle\}$
- (iv) $O_{SNS} = \{(0,0,1) : p \in \mathbb{X}\}$ 是 $\mathbb{X}$ 上的空 $SPH_N_S$
- (v) $I_{SNS} = \{(1,0,0) : p \in \mathbb{X}\}$ 是 $\mathbb{X}$ 上的全 $SPH_N_S$

### 15.2.3 SNS 之间的相似性量

两个 $SPH_N_S_s$ 与 $\mathcal{H}$ 之间的相似性定义为 $\varrho(\mathcal{G}, \mathcal{H}) = (\varrho_w(\mathcal{G}, \mathcal{H}), \varrho_i(\mathcal{G}, \mathcal{H}), \varrho_f(\mathcal{G}, \mathcal{H}))$，其中 $\varrho: SPH_N_S(\mathbb{X}) \times SPH_N_S(\mathbb{X}) \to [0,1]$ 满足以下属性：

- (i) $\varrho(\mathcal{G}, \mathcal{H}) = \varrho(B, A)$
- (ii) 对于所有 $\mathcal{G}, \mathcal{H} \in SPH_N_S(\mathbb{X})$，若 $A=B$ 则 $\varrho(\mathcal{G}, \mathcal{H}) = 1_{SNS}$
- (iii) $\varrho_w(\mathcal{G}, \mathcal{H}) \geq 0$ 且 $\varrho_i(\mathcal{G}, \mathcal{H}) \geq 0$
- (iv) 如果对于所有 $\mathcal{G}, \mathcal{D} \in SPH_N_S(\mathbb{X})$ 有 $\mathcal{G} \subseteq \mathcal{D}$，则 $\varrho(\mathcal{G}, \mathcal{H}) \geq \varrho(\mathcal{G}, \mathcal{D})$ 且 $\varrho(\mathcal{H}, \mathcal{D}) \geq \varrho(\mathcal{G}, \mathcal{D})$

其中 $\varrho_w(\mathcal{G}, \mathcal{H}), \varrho_i(\mathcal{G}, \mathcal{H})$ 和 $\varrho_f(\mathcal{G}, \mathcal{H})$ 分别代表 $\mathcal{G}$ 与 $\mathcal{H}$ 之间的 $\mathbb{T}, \mathbb{I}$ 和 $\mathbb{F}$ 相似性程度。

## 使用球形中性相似性进行 MCDM 建模

### 15.2.4 三角函数相似性量

设 $\mathcal{M}$ 和 $\mathcal{L}$ 是 $\mathbb{X}$ 上任意两个 $SPH_N_S$。那么三种正切、余弦和余切相似性量定义为：

- (i) $TAN_S(\mathcal{M}, \mathcal{L}) = \frac{1}{n} \sum_{i=1}^{n} [tan\left(\frac{\pi}{2}\right)|\mathcal{M}_i(p_i) - \mathcal{L}_i(p_i)| + |\mathcal{M}_f(p_i) - \mathcal{L}_f(p_i)| + |\mathcal{M}_g(p_i) - \mathcal{L}_g(p_i)|]$
- (ii) $COT\_S(\mathcal{M}, \mathcal{L}) = \frac{1}{n} \sum_{i=1}^{n} [cot\left(\frac{\pi}{4}\right)|\mathcal{M}_i(p_i) - \mathcal{L}_i(p_i)| + |\mathcal{M}_f(p_i) - \mathcal{L}_f(p_i)| + |\mathcal{M}_g(p_i) - \mathcal{L}_g(p_i)|]$
- (iii) $COS\_S(\mathcal{M}, \mathcal{L}) = \frac{1}{n} \sum_{i=1}^{n} \frac{\mathcal{M}_i(p_i) \cdot \mathcal{L}_i(p_i) + |\mathcal{M}_f(p_i) \cdot \mathcal{L}_f(p_i)| + |\mathcal{M}_g(p_i) \cdot \mathcal{L}_g(p_i)|}{\sqrt{\mathcal{M}_i(p_i)^2 + \mathcal{L}_i(p_i)^2} \cdot \sqrt{\mathcal{M}_f(p_i)^2 + \mathcal{L}_f(p_i)^2}}$

### 15.2.5 三角相似性量的性质

定理 2.5.1 设 $\mathcal{M}$ 和 $\mathcal{L}$ 是 $\mathbb{X}$ 上任意两个 $SPH_N_S$。那么

- (i) $TAN_S(\mathcal{M}, \mathcal{L}) \leq 1$
- (ii) 仅当 $\mathcal{M} = \mathcal{L}$ 时，$TAN_S(\mathcal{M}, \mathcal{L}) = 1$
- (iii) $TAN_S(\mathcal{M}, \mathcal{L}) = TAN_S(\mathcal{L}, \mathcal{M})$
- (iv) 如果 $Q$ 是 $\mathbb{X}$ 中的 $SPH_N_S$ 且 $\mathcal{Q} \subseteq \mathcal{L}$，则 $TAN_S(\mathcal{M}, Q) \leq TAN_S(\mathcal{M}, \mathcal{L})$ 且 $TAN_S(\mathcal{L}, Q) \leq TAN_S(\mathcal{L}, \mathcal{Q})$

证明：

- (i) $\mathbb{T}, \mathbb{I},$ 和 $\mathbb{F}$ 处于 0 和 1 之间。因此，$TAN_S(\mathcal{M}, \mathcal{L}) \leq 1$。
- (ii) 对于任意两个 $SPH_N_S$ $\mathcal{M}$ 和 $\mathcal{L}$，$\mathcal{M} = \mathcal{L} \Rightarrow \mathcal{M}_i(x) = \mathcal{L}_i(x)$ 且 $\mathcal{M}_f(x) = \mathcal{L}_f(x)$。因此，$TAN_S(\mathcal{M}, \mathcal{L}) = 1$。反之，如果 $TAN_S(\mathcal{M}, \mathcal{L}) = 1 \Rightarrow |\mathcal{M}_i(p_i) - \mathcal{L}_i(p_i)| = |\mathcal{M}_f(p_i) - \mathcal{L}_f(p_i)| = |\mathcal{M}_g(p_i) - \mathcal{L}_g(p_i)| = 0$。因此，$\mathcal{M} = \mathcal{L}$。
- (iii) 证明显而易见。
- (iv) 由于 $\mathcal{M}_{\gamma}(p) \ge \mathcal{Q}_{\gamma}(p) \le \mathcal{L}_{\gamma}(p)$$\mathcal{M}_{\gamma}(p) \le \mathcal{Q}_{\gamma}(p)$ 且 $\mathcal{M}_{\gamma}(p) \ge \mathcal{Q}_{\gamma}(p) \ge \mathcal{L}_{\gamma}(p)$$\Rightarrow |\mathcal{M}_{\gamma}(p) - \mathcal{L}_{\gamma}(p)| \le |\mathcal{M}_{\gamma}(p) - \mathcal{Q}_{\gamma}(p)|$ 且 $|\mathcal{Q}_{\gamma}(p) - \mathcal{L}_{\gamma}(p)| \ge |\mathcal{M}_{\gamma}(p) - \mathcal{Q}_{\gamma}(p)|$。

定理 2.5.2 设 $\mathcal{M}$ 和 $\mathcal{L}$ 是 $\mathbb{X}$ 上任意两个 $SPH_N_S$。那么

- (i) $COS_S(\mathcal{M}, \mathcal{L}) \leq 1$
- (ii) 仅当 $\mathcal{M} = \mathcal{L}$ 时，$COS_S(\mathcal{M}, \mathcal{L}) = 1$
- (iii) $COS_S(\mathcal{M}, \mathcal{L}) = COS_S(\mathcal{L}, \mathcal{M})$
- (iv) 如果 $Q$ 是 $\mathbb{X}$ 中的 $SPH_N_S$ 且 $\mathcal{Q} \subseteq \mathcal{L}$，则 $COS_S(\mathcal{M}, Q) \leq COS_S(\mathcal{M}, \mathcal{L})$ 且 $COS_S(\mathcal{L}, Q) \leq COS_S(\mathcal{L}, \mathcal{Q})$

证明：

- (i) $\mathbb{T}, \mathbb{I},$ 和 $\mathbb{F}$ 处于 0 和 1 之间。因此，$COS_S(\mathcal{M}, \mathcal{L}) \leq 1$。
- (ii) 对于任意两个 $SPH_N_S$ $\mathcal{M}$ 和 $\mathcal{L}$，$\mathcal{M} = \mathcal{L} \Rightarrow \mathcal{M}_i(x) = \mathcal{L}_i(x)$ 且 $\mathcal{M}_f(x) = \mathcal{L}_f(x)$。因此，$COS_S(\mathcal{M}, \mathcal{L}) = 1$。反之，如果 $COS_S(\mathcal{M}, \mathcal{L}) = 1 \Rightarrow |\mathcal{M}_i(p_i) - \mathcal{L}_i(p_i)| = |\mathcal{M}_f(p_i) - \mathcal{L}_f(p_i)| = |\mathcal{M}_g(p_i) - \mathcal{L}_g(p_i)| = 0$。因此，$\mathcal{M} = \mathcal{L}$。
- (iii) 证明显而易见。
- (iv) 由于 $\mathcal{M}_{\gamma}(p) \ge \mathcal{Q}_{\gamma}(p) \le \mathcal{L}_{\gamma}(p)$$\mathcal{M}_{\gamma}(p) \le \mathcal{Q}_{\gamma}(p)$ 且 $\mathcal{M}_{\gamma}(p) \ge \mathcal{Q}_{\gamma}(p) \ge \mathcal{L}_{\gamma}(p)$。

定理 2.5.3 设 $\mathcal{M}$ 和 $\mathcal{L}$ 是 $\mathbb{X}$ 上任意两个 $SPH_N_S$。那么

- (i) $COT_S(\mathcal{M}, \mathcal{L}) \leq 1$
- (ii) 仅当 $\mathcal{M} = \mathcal{L}$ 时，$COT_S(\mathcal{M}, \mathcal{L}) = 1$
- (iii) $COT_S(\mathcal{M}, \mathcal{L}) = COT_S(\mathcal{L}, \mathcal{M})$
- (iv) 如果 $Q$ 是 $\mathbb{X}$ 中的 $SPH_N_S$ 且 $\mathcal{Q} \subseteq \mathcal{L}$，则 $COT_S(\mathcal{M}, Q) \leq COT_S(\mathcal{M}, \mathcal{L})$ 且 $COT_S(\mathcal{L}, Q) \leq COT_S(\mathcal{L}, \mathcal{Q})$

## 15.3 决策算法

