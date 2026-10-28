
回顾：$r = |I \cap S^C|$，其中 $I \setminus S = I \cap S^C$。因此，由 (C.4) 和 (C.5)，存在一个从 $I \setminus S$ 到 $(I^- \cap S) \times (I^+ \cap S)$ 的单射。令 $\psi$ 为这样的映射。对每个 $i \in I \setminus S$，记 $\psi(i) := (\psi^-(i), \psi^+(i))$，其中 $(\psi^-(i), \psi^+(i)) \in (I^- \cap S) \times (I^+ \cap S)$。考虑任意 $i \in I \setminus S$。根据 $I^-$ 和 $I^+$ 的定义，有

$v_{\psi^-(i)} \le v_i \le v_{\psi^+(i)}.$

因此，对任意实数值 $u$，

$|v_i - u| \le \max \{ |v_{\psi^+(i)} - u|, |v_{\psi^-(i)} - u| \}.$

对所有 $i \in I \setminus S$，定义 $\phi$ 为 $\phi(i) = \operatorname{argmax}_{j \in \{\psi^+(i), \psi^-(i)\}} |v_j - \bar{v}_S|$，则可得 (C.3) 成立，从而完成证明。$\square$

利用引理 C.2 和 C.3，我们现在可以在下文中证明 CWTM$_q$ 是一个 $(q, \kappa)$-鲁棒平均。

### 命题 C.1
设 $n \in \mathbb{N}^*$ 且 $q < n/2$。CWTM$_q$ 是 $(q, \kappa)$-鲁棒的，其中

$\kappa = \frac{6q}{n - 2q} \left(1 + \frac{q}{n - 2q}\right).$

**证明** 首先，注意 CWTM$_q$ 是一种逐坐标聚合，其精确含义如引理 C.2 所定义。因此，根据引理 C.2，只需证明截尾均值在标量域（即 $d = 1$）上是 $(q, \kappa)$-鲁棒的。

考虑 $n$ 个任意值 $v_1, \dots, v_n \in \mathbb{R}$。不失一般性，假设 $v_1 \le \dots \le v_n$。记 $I := \{q+1, \dots, n - q\}$，并令 $S \subseteq [n]$ 是大小为 $n - q$ 的任意集合。回顾根据截尾均值的定义，有 TM$_q(v_1, \dots, v_n) = \frac{1}{n - 2q} \sum_{i \in I} v_i$。因此，

$|\text{TM}_q(v_1, \dots, v_n) - \bar{v}_S|^2 = \left| \frac{1}{n - 2q} \sum_{i \in I} v_i - \bar{v}_S \right|^2 = \left| \frac{1}{n - 2q} \sum_{i \in I} (v_i - \bar{v}_S) \right|^2$

$= \left| \frac{1}{n - 2q} \sum_{i \in I} (v_i - \bar{v}_S) - \frac{1}{n - 2q} \sum_{i \in S} (v_i - \bar{v}_S) \right|^2 \quad \left( \because \sum_{i \in S} (v_i - \bar{v}_S) = 0 \right)$

$= \frac{1}{(n - 2q)^2} \left| \sum_{i \in I \setminus S} (v_i - \bar{v}_S) - \sum_{i \in S \setminus I} (v_i - \bar{v}_S) \right|^2.$

其中平局可以任意打破。$\mathrm{Krum}_q (\mathbf{v}_1, \dots, \mathbf{v}_n)$ 输出向量 $\mathbf{v}_{k^*}$，使得

$$k^* \in \operatorname*{argmin}_{j \in [n]} \sum_{i \in N_j} \|\mathbf{v}_j - \mathbf{v}_i\|^2.$$

### 命题 C.2
*设* $n \in \mathbb{N}^*$ *且* $q < \frac{n}{2}$。*则* $\mathrm{Krum}_q$ *是* $(q, \kappa)$*-鲁棒的，其中* $\kappa = 6 \left(1 + \frac{q}{n-2q}\right)$。

***证明*** 设 $n \in \mathbb{N}^*$，$q < \frac{n}{2}$，且 $\mathbf{v}_1, \dots, \mathbf{v}_n \in \mathbb{R}^d$。考虑任意大小为 $|S| = n - q$ 的子集 $S \subseteq [n]$。在下文中，对每个 $j \in [n]$，用 $N_j$ 表示 $\mathbf{v}_j$ 在 $\{\mathbf{v}_1, \dots, \mathbf{v}_n\}$ 中 $n - q$ 个最近邻的下标集合，其中平局任意打破。注意这意味着对所有 $j \in [n]$，有

$$\sum_{i \in N_j} \|\mathbf{v}_j - \mathbf{v}_i\|^2 \leq \sum_{i \in S} \|\mathbf{v}_j - \mathbf{v}_i\|^2. \tag{C.7}$$

令 $k^* \in [n]$ 为 $\mathrm{Krum}_q$ 选择的下标，即 $k^* \in \operatorname*{argmin}_{j \in [n]} \sum_{i \in N_j} \|\mathbf{v}_j - \mathbf{v}_i\|^2$。因此，由 (C.7)，有

$$\sum_{i \in N_{k^*}} \|\mathbf{v}_{k^*} - \mathbf{v}_i\|^2 = \min_{j \in [n]} \sum_{i \in N_j} \|\mathbf{v}_j - \mathbf{v}_i\|^2 \leq \min_{j \in S} \sum_{i \in N_j} \|\mathbf{v}_j - \mathbf{v}_i\|^2$$

$$\leq \frac{1}{|S|} \sum_{j \in S} \sum_{i \in N_j} \|\mathbf{v}_j - \mathbf{v}_i\|^2 \leq \frac{1}{|S|} \sum_{j \in S} \sum_{i \in S} \|\mathbf{v}_j - \mathbf{v}_i\|^2. \tag{C.8}$$

注意

$$\sum_{j \in S} \sum_{i \in S} \|\mathbf{v}_j - \mathbf{v}_i\|^2 = \sum_{i,j \in S} \|\mathbf{v}_j - \bar{\mathbf{v}}_S - (\mathbf{v}_i - \bar{\mathbf{v}}_S)\|^2$$

$$= \sum_{i,j \in S} \left( \|\mathbf{v}_j - \bar{\mathbf{v}}_S\|^2 + \|\mathbf{v}_i - \bar{\mathbf{v}}_S\|^2 - 2 \langle \mathbf{v}_j - \bar{\mathbf{v}}_S, \mathbf{v}_i - \bar{\mathbf{v}}_S \rangle \right)$$

$$= 2|S| \sum_{i \in S} \|\mathbf{v}_i - \bar{\mathbf{v}}_S\|^2 - 2 \sum_{i \in S} \left( \sum_{j \in S} \langle \mathbf{v}_j - \bar{\mathbf{v}}_S, \mathbf{v}_i - \bar{\mathbf{v}}_S \rangle \right).$$

在上式中，对所有 $i \in S$，有 $\sum_{j \in S} \langle \mathbf{v}_j - \bar{\mathbf{v}}_S, \mathbf{v}_i - \bar{\mathbf{v}}_S \rangle = \langle \mathbf{0}, \mathbf{v}_i - \bar{\mathbf{v}}_S \rangle = 0$。因此，

$$\sum_{j \in S} \sum_{i \in S} \|\mathbf{v}_j - \mathbf{v}_i\|^2 \leq 2|S| \sum_{i \in S} \|\mathbf{v}_i - \bar{\mathbf{v}}_S\|^2.$$

## C 鲁棒系数的推导

将上式代入 (C.8)，可得

$$\sum_{i \in N_{k^*}} \|\mathbf{v}_{k^*} - \mathbf{v}_i\|^2 \leq 2 \sum_{i \in S} \|\mathbf{v}_i - \bar{\mathbf{v}}_S\|^2 \, . \tag{C.9}$$

考虑任意 $i \in S$。由三角不等式和 Jensen 不等式，有

$$\|\mathbf{v}_{k^*} - \bar{\mathbf{v}}_S\|^2 \leq (\|\mathbf{v}_{k^*} - \mathbf{v}_i\| + \|\mathbf{v}_i - \bar{\mathbf{v}}_S\|)^2 \leq 2\,\|\mathbf{v}_{k^*} - \mathbf{v}_i\|^2 + 2\,\|\mathbf{v}_i - \bar{\mathbf{v}}_S\|^2 \, .$$

对上式重新整理各项，可得

$$\|\mathbf{v}_{k^*} - \mathbf{v}_i\|^2 \geq \frac{1}{2} \|\mathbf{v}_{k^*} - \bar{\mathbf{v}}_S\|^2 - \|\mathbf{v}_i - \bar{\mathbf{v}}_S\|^2 \, .$$

上式结合 $|S \cap N_{k^*}| = |S| + |N_{k^*}| - |S \cup N_{k^*}| \geq (n-q) + (n-q) - n = n - 2q$ 这一事实，意味着

$$\begin{aligned} \sum_{i \in S \cap N_{k^*}} \|\mathbf{v}_{k^*} - \mathbf{v}_i\|^2 &\geq \frac{|S \cap N_{k^*}|}{2} \|\mathbf{v}_{k^*} - \bar{\mathbf{v}}_S\|^2 - \sum_{i \in S \cap N_{k^*}} \|\mathbf{v}_i - \bar{\mathbf{v}}_S\|^2 \\ &\geq \frac{n-2q}{2} \|\mathbf{v}_{k^*} - \bar{\mathbf{v}}_S\|^2 - \sum_{i \in S \cap N_{k^*}} \|\mathbf{v}_i - \bar{\mathbf{v}}_S\|^2 \, . \end{aligned}$$

由于 $\sum_{i \in N_{k^*}} \|\mathbf{v}_{k^*} - \mathbf{v}_i\|^2 \geq \sum_{i \in S \cap N_{k^*}} \|\mathbf{v}_{k^*} - \mathbf{v}_i\|^2$，由上式可得

$$\sum_{i \in N_{k^*}} \|\mathbf{v}_{k^*} - \mathbf{v}_i\|^2 \geq \frac{n-2q}{2} \|\mathbf{v}_{k^*} - \bar{\mathbf{v}}_S\|^2 - \sum_{i \in S \cap N_{k^*}} \|\mathbf{v}_i - \bar{\mathbf{v}}_S\|^2 \, .$$

将上式代入 (C.9)，可得

$$\frac{n-2q}{2} \|\mathbf{v}_{k^*} - \bar{\mathbf{v}}_S\|^2 - \sum_{i \in S \cap N_{k^*}} \|\mathbf{v}_i - \bar{\mathbf{v}}_S\|^2 \leq 2 \sum_{i \in S} \|\mathbf{v}_i - \bar{\mathbf{v}}_S\|^2 \, .$$

在上式中使用 $\sum_{i \in S \cap N_{k^*}} \|\mathbf{v}_{k^*} - \mathbf{v}_i\|^2 \leq \sum_{i \in S} \|\mathbf{v}_{k^*} - \mathbf{v}_i\|^2$，可得

$$\frac{n-2q}{2} \|\mathbf{v}_{k^*} - \bar{\mathbf{v}}_S\|^2 \leq 3 \sum_{i \in S} \|\mathbf{v}_i - \bar{\mathbf{v}}_S\|^2 \, .$$

因此，回顾 $|S| = n-q$，由上式可得

$$\|\mathbf{v}_{k^*} - \bar{\mathbf{v}}_S\|^2 \leq \frac{6(n-q)}{n-2q} \frac{1}{|S|} \sum_{i \in S} \|\mathbf{v}_i - \bar{\mathbf{v}}_S\|^2 \, .$$

证明完毕。

### C.4 几何中位数

向量 **v**₁, …, **v**ₙ ∈ ℝᵈ 的*几何中位数*，记为 GeoMed，定义为最小化这些向量的欧几里得距离之和的向量。具体地，

GeoMed(**v**₁, …, **v**ₙ) ∈ argmin_{**y**∈ℝᵈ} ∑_{i=1}^n ‖**y** − **v**ᵢ‖.

### 命题 C.3
*设 n ∈ ℕ 且 q < n/2。几何中位数是 (q, κ)-鲁棒的，其中 κ = 4 (1 + q/(n−2q))²。*

*证明* 记 **v*** := GeoMed(**v**₁, …, **v**ₙ) 为输入向量的几何中位数。考虑任意大小为 |S| = n − q 的子集 S ⊆ [n]。由三角不等式，对所有 i ∈ S，有

‖**v*** − **v**ᵢ‖ ≥ ‖**v*** − **\bar{v}**ₛ‖ − ‖**v**ᵢ − **\bar{v}**ₛ‖. (C.10)

类似地，对任意 i ∈ [n] \ S，有

‖**v*** − **v**ᵢ‖ ≥ ‖**v**ᵢ − **\bar{v}**ₛ‖ − ‖**v*** − **\bar{v}**ₛ‖. (C.11)

将所有输入向量对应的 (C.10) 和 (C.11) 相加，可得

∑_{i∈[n]} ‖**v*** − **v**ᵢ‖ ≥ (n − 2q) ‖**v*** − **\bar{v}**ₛ‖ + ∑_{i∈[n]\S} ‖**v**ᵢ − **\bar{v}**ₛ‖ − ∑_{i∈S} ‖**v**ᵢ − **\bar{v}**ₛ‖.

