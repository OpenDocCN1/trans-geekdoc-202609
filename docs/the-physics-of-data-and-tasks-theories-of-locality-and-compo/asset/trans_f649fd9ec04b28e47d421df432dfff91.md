

## A.3 卷积核与局部核的 Mercer 分解

一般情况下，

```
$\int_{[0,1]^d} d^x d^y K^{LC}(x,y) e^{\mathbf{k}_l^T x} e^{\mathbf{k}_k^T y} = \sum_{i=1}^d \lambda_i \int_{[0,1]^d} d^x d^y \lambda_q e^{\mathbf{q}_i^T (x-y)} e^{\mathbf{k}_k^T y}$
= \frac{1}{2} \sum_{q \in P_l} \lambda_q \delta(\mathbf{k}_l, \mathbf{q}) + \sum_{i \in P_l} \delta(\mathbf{k}_l, \mathbf{0})
+ \sum_{i \in P_i} \epsilon^q e^{\mathbf{q}_i^T x} \delta(\mathbf{k}_l^{(s)}, \mathbf{0}) \delta(\mathbf{k}_{s-o+1}^{(o)}, \mathbf{q}_i) \delta(\mathbf{q}_{o+1}^{(s-o)}, \mathbf{0})$
+ \sum_{i \in P_i} \epsilon^q e^{\mathbf{q}_i^T x} \delta(\mathbf{k}_l^{(s)}, \mathbf{0}) \delta(\mathbf{k}_{s-o+1}^{(o)}, \mathbf{0}) \quad (155)
```

对于 $k \in \mathcal{F}^u$，其中 $u=1, \dots, s$，当满足以下条件时，将 $k$ 的第一个分量置为 0 的 delta 函数成立：

```
$\int_{[0,1]^d} d^x d^y K^{LC}(x,y) e^{\mathbf{k}_l^T x} e^{\mathbf{k}_k^T y} = \frac{1}{2} \sum_{q \in P_l} \lambda_q \delta(\mathbf{k}_l, \mathbf{q}) e^{\mathbf{k}_k^T y} + \sum_{q} \epsilon^q e^{\mathbf{q}_i^T x} \delta(\mathbf{k}_l^{(s)}, \mathbf{0}) \delta(\mathbf{k}_{s-o+1}^{(o)}, \mathbf{0}) \quad (156)
```

对于 $k \in \mathcal{F}^s$，括号中的第二项消失，且特征方程满足 $\lambda_k = \Lambda_k/d$。对于 $\mathbf{k} = \mathbf{k}^{(u)}$ 且 $u < s$，对于任何 $o \geq u$，$\delta(\mathbf{k}^{(s-u)}, \mathbf{0}) = 0$。由于余项的影响，方程 156 的右侧变为对所有为 $s-u+1$ 的 $q$（包括 $k^{(u)}$ 本身）的求和。在指数中与 $q$ 相乘的补丁 $\mathbf{x}_l$ 也是 $\mathbf{x}_l$ 的位移，因此和中的所有因子 $e^{\mathbf{q}_i^T \mathbf{x}_l}$ 都与 $e^{\mathbf{k}^{(u)T} \mathbf{x}_l}$ 重合。由于 $\lambda_q$ 取决于 $q$ 的模，所有这些项对应于同一个特征值 $\lambda_k$，因此：

```
$\int_{[0,1]^d} d^x d^y K^{LC}(x,y) e^{\mathbf{k}_k^T y} = \frac{s-u+1}{d} \Lambda_{k^{(u)}} e^{\mathbf{k}^{(u)T} \mathbf{x}_l} \quad (157)
```

我们证明核 149 的展开式：

```
$K^{LC}(x,y) = \frac{1}{d} \sum_{i \in P_l} C(x,y) = \frac{1}{d} \sum_{i \in P_l} \lambda_k \phi_k(\mathbf{x}_i) \phi_k(\mathbf{y}_i) \quad (158)
```

与卷积核特征分解的证明一样，所有具有 $s-u$ 个消零分量的 $k$ 都可以写成 $k^{(u)} \in \mathcal{F}^u$ 的位移，其最后 $s-u$ 个分量为零。$k$ 的位移不影响 $\lambda_k$，也不影响乘积 $\phi_k(\mathbf{x}_i)\phi_k(\mathbf{y}_i)$，在对 $i$ 求和后会导致特征值的简并，这通过将 $k$ 的求和限制在 $\mathcal{F}^u, u \leq s$ 来消除，并用因子 $(s-u+1)/d$ 重新缩放剩余的特征值 $\lambda_k$，从而得到方程 149。

## 附录：局部性击败维度灾难

## A.4 定理 2.4.1 的证明

**定理 A.1（正文定理）。** 设 $K_T$ 为 $d$ 维卷积核，具有平移不变的 $t$ 维组成分量，且在原点的非解析性由指数 $a_t > 0$ 控制。设 $K_S$ 为 $d$ 维卷积核或局部学生核，具有平移不变的 $s$ 维组成分量，且在原点的非解析性由指数 $a_s > 0$ 控制。此外假设，如果核具有不重叠的补丁，则 $s \ge 1$ 是 $t$ 的整数倍；且在 $d$ 维环面上均匀分布。那么，在 $P \to \infty$ 的极限下，存在以下渐近等价：

$B(P) \sim P^{-\beta}, \quad \beta = a_s/t.$

证明。为了清晰起见，我们从不重叠补丁的证明开始，并将其扩展到重叠补丁的情况。由于 $K_T$ 和 $K_S$ 具有平移不变的组成核且数据在 $d$ 维环面上均匀分布，这些核可以在傅里叶空间中对角化。让我们先考虑一个卷积学生：由于组成核的同向性，$K_S$ 的傅里叶系数 $\Lambda_k^{(s)}$ 取决于 $|k|$。注意表示组成分维度的上标。特别是 $\Lambda_k^{(s)}$ 是 $k$ 的减函数，且对于较大的 $k$，$\Lambda_k \sim k^{-(s+1)}$。那么，$B(P)$

```
$B(P) = \sum_{k} \Lambda_k^{(s)} \dots$
```
（注：此处原文公式不完整，翻译遵循原文结构）

