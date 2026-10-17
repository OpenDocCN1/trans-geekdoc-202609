
### 引理 5.3.2
设 $\mathbf{0}_1, \mathbf{0}_2, l_0, l_1, l_2 \in \mathbb{N}$，设 $A : \mathbb{R}^{l_1} \times \mathbb{R}^{l_2} \times \mathbb{R}^{l_0} \to \mathbb{R}^{l_2} \times \mathbb{R}^{l_1+l_0}$ 和 $B : \mathbb{R}^{l_2} \times \mathbb{R}^{l_1+l_0} \to \mathbb{R}^{l_2} \times \mathbb{R}^{l_1}$ 满足对于所有 $\theta_1 \in \mathbb{R}^{l_1}$、$\theta_2 \in \mathbb{R}^{l_2}$ 和 $x \in \mathbb{R}^{l_0}$，有

$$A(\theta_1, \theta_2, x) = (\theta_2, (\theta_1, x)) \quad\text{且}\quad B(\theta_2, (\theta_1, x)) = (\theta_2, F_1(\theta_1, x)),\tag{5.25}$$

对于每个 $k \in \{1, 2\}$，设 $F_k : \mathbb{R}^{l_k} \times \mathbb{R}^{l_k-1} \to \mathbb{R}^{l_k}$ 是可微的；设 $f : \mathbb{R}^{l_1} \times \mathbb{R}^{l_2} \times \mathbb{R}^{l_0} \to \mathbb{R}^{l_2}$ 满足对于所有 $\theta_1 \in \mathbb{R}^{l_1}$、$\theta_2 \in \mathbb{R}^{l_2}$ 和 $x \in \mathbb{R}^{l_0}$，有

$$f(\theta_1, \theta_2, x) = (F_2(\theta_2, \cdot) \circ F_1(\theta_1, \cdot))(x).\tag{5.26}$$

*那么*

- (i) 有 $f = F_2 \circ B \circ A$ 成立，且
- (ii) $f$ 是可微的。

*引理 5.3.2 的证明。* 注意，(5.25) 和 (5.26) 确保对于所有 $\theta_{1} \in \mathbb{R}^{l_{1}}$、$\theta_{2} \in \mathbb{R}^{l_{2}}$ 和 $x \in \mathbb{R}^{l_{0}}$，均有

$$f(\theta_{1},\theta_{2},x)=F_{2}(\theta_{2},F_{1}(\theta_{1},x))=F_{2}(B(\theta_{2},\theta_{1},x))=F_{2}(B(A(\theta_{1},\theta_{2},x))). \qquad (5.27)$$

观察可知，引理 5.3.1（在引理 5.3.1 的记号下，取 $l_{1} \mapsto l_{2}$、$l_{2} \mapsto l_{1}+l_{0}$、$F_{1} \mapsto (\mathbb{R}^{l_{2}} \ni \theta_{2} \mapsto \theta_{2} \in \mathbb{R}^{l_{2}})$、$F_{2} \mapsto (\mathbb{R}^{l_{1}+l_{0}} \ni (\theta_{1},x) \mapsto F_{1}(\theta_{1},x) \in \mathbb{R}^{l_{1}})$）蕴含 $B$ 是可微的。结合这一点、$A$ 是可微的事实、$F_{2}$ 是可微的事实以及 (5.27)，利用链式法则可知 $f$ 是可微的。至此，引理 5.3.2 的证明完成。

## 5.3.2 关于人工神经网络实现的可微性

### 引理 5.3.3
*人工神经网络* 实现函数的可微性。设 $L \in \mathbb{N}$，$l_{0}$、$l_{1}$、...、$l_L \in \mathbb{N}$；对于每个 $k \in \{1, 2, ..., L\}$，设 $d_k = l_k(l_k + 1)$；对于每个 $k \in \{1, 2, ..., L\}$，设 $\Psi_{k} : \mathbb{R}^{l_{k}} \rightarrow \mathbb{R}^{l_{k}}$ 是可微的；对于每个 $k \in \{1, 2, ..., L\}$，设 $F_k: \mathbb{R}^{d_{k}} \times \mathbb{R}^{l_{k-1}} \rightarrow \mathbb{R}^{l_{k}}$ 满足对于所有 $\theta \in \mathbb{R}^{d_{k}}$ 和 $x \in \mathbb{R}^{l_{k-1}}$，有

$$F_{k}(\theta,x)=\Psi_{k}(A_{l_{k},l_{k-1}}^{\theta,0}(x)) \qquad (5.28)$$

*(参见定义 1.1.1)*。那么

- (i) 对于所有 $\theta_{1} \in \mathbb{R}^{d_{1}}$、$\theta_{2} \in \mathbb{R}^{d_{2}}$、...、$\theta_{L} \in \mathbb{R}^{d_{L}}$ 和 $x \in \mathbb{R}^{l_{0}}$，均有

$$\big(\mathcal{N}_{\Psi_{1},\Psi_{2},\ldots,\Psi_{L}}^{\theta_{1},\theta_{2},\ldots,\theta_{L},l_{0}}\big)(x)=\big(F_{L}(\theta_{L},\cdot) \circ F_{L-1}(\theta_{L-1},\cdot) \circ \cdots \circ F_{1}(\theta_{1},\cdot)\big)(x) \qquad (5.29)$$

- (ii) 函数

$$\mathbb{R}^{d_{1}+d_{2}+\cdots+d_{L}} \times \mathbb{R}^{l_{0}} \ni (\theta,x) \mapsto \big(\mathcal{N}_{\Psi_{1},\Psi_{2},\ldots,\Psi_{L}}^{\theta,l_{0}}\big)(x) \in \mathbb{R}^{l_{L}} \qquad (5.30)$$

是可微的

*(参见定义 1.1.3)*。

*引理 5.3.3 的证明。* 注意，(1.1) 表明对于所有 $\theta_{1} \in \mathbb{R}^{d_{1}}$、$\theta_{2} \in \mathbb{R}^{d_{2}}$、...、$\theta_{L} \in \mathbb{R}^{d_{L}}$ 和 $k \in \{1, 2, ..., L\}$，均有

$$\mathcal{A}_{l_{k},l_{k-1}}^{(\theta_{1},\theta_{2},\ldots,\theta_{L}),\sum_{j=1}^{k-1}d_{j}}=\mathcal{A}_{l_{k},l_{k-1}}^{\theta_{k},0}. \qquad (5.31)$$

因此，我们得到对于所有 $\theta_{1} \in \mathbb{R}^{d_{1}}$、$\theta_{2} \in \mathbb{R}^{d_{2}}$、...、$\theta_{L} \in \mathbb{R}^{d_{L}}$ 和 $k \in \{1, 2, ..., L\}$，均有

$$F_{k}(\theta_{k},x)=\big(\Psi_{k} \circ \mathcal{A}_{l_{k},l_{k-1}}^{(\theta_{1},\theta_{2},\ldots,\theta_{L}),\sum_{j=1}^{k-1}d_{j}}\big)(x). \qquad (5.32)$$

## 5.4 损失函数

### 5.4.1 绝对误差损失

#### 引理 5.3.4
**经验风险函数的可微性。** 设 $\mathfrak{L}, \mathfrak{d} \in \mathbb{N}\setminus\{1\}$，$M, l_0$，$l_1, \dots, l_L \in \mathbb{N}$，$x_1, x_2, \dots, x_M \in \mathbb{R}^{\mathfrak{d}_0}$，$y_1, y_2, \dots, y_M \in \mathbb{R}^{\mathfrak{d}_L}$ 满足 $\mathfrak{d} = \sum_{k=1}^{L} l_k (l_{k-1}+1)$。对于每个 $k \in \{1, 2, \dots, L\}$，设 $\Psi_k\colon \mathbb{R}^{l_k} \to \mathbb{R}^{l_{k}}$ 可微，并且设 $\mathcal{L}\colon \mathbb{R}^{\mathfrak{d}} \to \mathbb{R}$ 满足：对于所有 $\theta \in \mathbb{R}^{\mathfrak{d}}$，有

$$ \mathcal{L}(\theta) = \frac{1}{M} \left[ \sum_{m=1}^{M} \mathbf{L}\big( ( \mathcal{N}_{\Psi_1, \Psi_2, \dots, \Psi_L}^{\theta_{l_0}} )(x_m), y_m \big) \right] $$

（参见定义 1.1.3）。则 $\mathcal{L}$ 是可微的。

*引理 5.3.4 的证明。* 注意，引理 5.3.3 和引理 5.3.1（在引理 5.3.1 的记号中，取 $\mathfrak{d}_1 \frown \mathfrak{d} + l_0$，$\mathfrak{d}_2 \frown l_L$，$l_1 \frown l_L$，$l_2 \frown l_L$，$F_1 \frown (\mathbb{R}^{\mathfrak{d}} \times \mathbb{R}^{l_0} \ni (\theta, x) \to ( \mathcal{N}_{\Psi_1, \Psi_2, \dots, \Psi_L}^{\theta_{l_0}} )(x) \in \mathbb{R}^{l_L}$，$F_2 \frown \text{id}_{\mathbb{R}^{l_L}}$）表明

$$ \mathbb{R}^{\mathfrak{d}} \times \mathbb{R}^{l_0} \times \mathbb{R}^{l_L} \ni (\theta, x, y) \to \big( ( \mathcal{N}_{\Psi_1, \Psi_2, \dots, \Psi_L}^{\theta_{l_0}} )(x), y \big) \in \mathbb{R}^{l_L} \times \mathbb{R}^{l_L} $$

是可微的。由于假设 $\mathbf{L}$ 是可微的，且根据链式法则，对于所有 $x \in \mathbb{R}^{\mathfrak{d}_0}$，$y \in \mathbb{R}^{\mathfrak{d}_L}$，均有

$$ \mathbb{R}^{\mathfrak{d}} \ni \theta \to \mathbf{L}\big( ( \mathcal{N}_{\Psi_1, \Psi_2, \dots, \Psi_L}^{\theta_{l_0}} )(x_m), y_m \big) \in \mathbb{R} $$

是可微的。这意味着 $\mathcal{L}$ 是可微的。至此，引理 5.3.4 的证明完成。

#### 引理 5.3.5
设 $a\colon \mathbb{R} \to \mathbb{R}$ 可微，且 $\mathfrak{d} \in D$。则 $\mathfrak{M}_{a,\mathfrak{d}}$ 是可微的。

*引理 5.3.5 的证明。* 注意到，假设 $a$ 可微、引理 5.3.1 以及归纳法表明：对于所有 $m \in \mathbb{N}$，$\mathfrak{M}_{a,m}$ 都是可微的。至此，引理 5.3.5 的证明完成。

#### 推论 5.3.6
设 $L, \mathfrak{o} \in \mathbb{N} \backslash \{1\}$，$M, l_0, l_1, \ldots, l_L \in \mathbb{N}$，$x_1, x_2, \ldots, x_M \in \mathbb{R}^{l_0}$，$y_1, y_2, \ldots, y_M \in \mathbb{R}^{l_L}$ 满足 $\mathfrak{o} = \sum_{k=1}^{L} l_k(l_{k-1} + 1)$。设 $a: \mathbb{R} \to \mathbb{R}$ 和 $\mathbf{L}: \mathbb{R}^{l} \times \mathbb{R}^{l} \to \mathbb{R}$ 可微，并且设 $\mathcal{L}: \mathbb{R}^{\mathfrak{o}} \to \mathbb{R}$ 满足：对于所有 $\theta \in \mathbb{R}^{\mathfrak{o}}$，有

$$\mathcal{L}(\theta) = \frac{1}{M} \left[ \sum_{m=1}^{M} \mathbf{L}\left( \left( \mathfrak{N}_{\mathfrak{m}_{a,l_1}^{\rho_0,l_0}, \mathfrak{m}_{a,l_2}, \ldots, \mathfrak{m}_{a,l_{L-1}}, \mathrm{id}_{\mathfrak{g}_{L}^{l}} \right) (x_m), y_m \right) \right] \tag{5.37}$$

（参见定义 1.1.3 和 1.2.1）。则 $\mathcal{L}$ 是可微的。

*推论 5.3.6 的证明。* 注意到，引理 5.3.5 和引理 5.3.4 证明了 $\mathcal{L}$ 是可微的。至此，推论 5.3.6 的证明完成。$\square$

#### 推论 5.3.7
设 $L, \mathfrak{o} \in \mathbb{N} \backslash \{1\}$，$M, l_0, l_1, \ldots, l_L \in \mathbb{N}$，$x_1, x_2, \ldots, x_M \in \mathbb{R}^{l_0}$，$y_1, y_2, \ldots, y_M \in (0, \infty)^{l_L}$ 满足 $\mathfrak{o} = \sum_{k=1}^{L} l_k(l_{k-1} + 1)$。设 $A$ 为 $l_L$ 维 softmax 激活函数，设 $a: \mathbb{R} \to \mathbb{R}$ 和 $\mathbf{L}: (0, \infty)^{l} \times (0, \infty)^{l} \to \mathbb{R}$ 可微，并且设 $\mathcal{L}: \mathbb{R}^{\mathfrak{o}} \to \mathbb{R}$ 满足：对于所有 $\theta \in \mathbb{R}^{\mathfrak{o}}$，有

$$\mathcal{L}(\theta) = \frac{1}{M} \left[ \sum_{m=1}^{M} \mathbf{L}\left( \left( \mathfrak{N}_{\mathfrak{m}_{a,l_1}^{\rho_0,l_0}, \mathfrak{m}_{a,l_2}, \ldots, \mathfrak{m}_{a,l_{L-1}}, A \right) (x_m), y_m \right) \right] \tag{5.38}$$

（参见定义 1.1.3、1.2.1、1.2.43 以及引理 1.2.44）。则 $\mathcal{L}$ 是可微的。

*推论 5.3.7 的证明。* 注意到，引理 5.3.5、$A$ 的可微性事实以及引理 5.3.4 共同建立了 $\mathcal{L}$ 的可微性。至此，推论 5.3.7 的证明完成。$\square$

#### 定义 5.4.1
设 $d \in \mathbb{N}$，设 $\|\cdot\|: \mathbb{R}^{d} \to [0, \infty)$ 是一个范数。当且仅当 $\mathbf{L}: \mathbb{R}^{d} \times \mathbb{R}^{d} \to \mathbb{R}$ 是从 $\mathbb{R}^{d} \times \mathbb{R}^{d}$ 到 $\mathbb{R}$ 的函数，并且对于所有 $x, y \in \mathbb{R}^{d}$ 满足

$$\mathbf{L}(x, y) = \|x - y\|. \tag{5.39}$$

时，我们称 $\mathbf{L}$ 是基于 $\|\cdot\|$ 的 $\ell^{1}$-误差损失函数（我们称 $\mathbf{L}$ 是基于 $\|\cdot\|$ 的绝对误差损失函数）。
