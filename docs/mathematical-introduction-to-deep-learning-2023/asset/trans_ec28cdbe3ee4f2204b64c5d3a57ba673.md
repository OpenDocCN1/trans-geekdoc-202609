
## 引理 6.3.3（动量项的显式表示）

设 $\mathbf{d} \in \mathbb{N}$，$(\alpha_n)_{n \in \mathbb{N}} \subseteq \mathbb{R}$，$(a_{n,k})_{(n,k) \in (\mathbb{N}_0)^2} \subseteq \mathbb{R}$，$(\mathscr{G}_n)_{n \in \mathbb{N}_0} \subseteq \mathbb{R}^\mathbf{d}$，$(\mathbf{m}_n)_{n \in \mathbb{N}_0} \subseteq \mathbb{R}^\mathbf{d}$ 满足对于所有 $n \in \mathbb{N}$，$\mathbf{k} \in \{0, 1, \dots, n-1\}$ 有

$$
\mathbf{m}_0 = \mathbf{0}, \quad \mathbf{m}_n = \alpha_n \mathbf{m}_{n-1} + (1 - \alpha_n)\mathscr{G}_{n-1}, \quad \text{且} \quad a_{n,k} = (1 - \alpha_{k+1}) \left[ \prod_{l=k+2}^{n} \alpha_l \right] \tag{6.196}
$$

则

- (i) 对于所有 $n \in \mathbb{N}_0$，有

$$
\mathbf{m}_n = \sum_{k=0}^{n-1} a_{n,k} \mathscr{G}_k \tag{6.197}
$$

- 并且
- (ii) 对于所有 $n \in \mathbb{N}_0$，有

$$
\sum_{k=0}^{n-1} a_{n,k} = 1 - \prod_{k=1}^{n} \alpha_k. \tag{6.198}
$$

### 引理 6.3.3 的证明

在整个证明过程中，设 $(m_n)_{n \in \mathbb{N}_0} \subseteq \mathbb{R}$ 满足对于所有 $n \in \mathbb{N}_0$ 有

$$
m_n = \sum_{k=0}^{n-1} a_{n,k}. \tag{6.199}
$$

现在我们通过对 $n \in \mathbb{N}_0$ 进行归纳法来证明第 (i) 项。对于基例 $n=0$，注意 (6.196) 确保

$$
\mathbf{m}_0 = \mathbf{0} = \sum_{k=0}^{-1} a_{n,k} \mathscr{G}_k. \tag{6.200}
$$

这确立了基例 $n=0$ 中的第 (i) 项。对于归纳步骤，注意 (6.196) 保证了对于所有 $\mathbf{m}_n = \sum_{k=0}^{n-1} a_{n,k} \mathscr{G}_k$ 的 $n \in \mathbb{N}_0$，都有

$$
\begin{split}
\mathbf{m}_{n+1} &= \alpha_{n+1} \mathbf{m}_n + (1 - \alpha_{n+1}) \mathscr{G}_n \\
&= \left[ \sum_{k=0}^{n-1} \alpha_{n+1} a_{n,k} \mathscr{G}_k \right] + (1 - \alpha_{n+1}) \mathscr{G}_n \\
&= \left[ \sum_{k=0}^{n-1} \alpha_{n+1} (1 - \alpha_{k+1}) \left[ \prod_{l=k+2}^{n} \alpha_l \right] \mathscr{G}_k \right] + (1 - \alpha_{n+1}) \mathscr{G}_n \\
&= \left[ \sum_{k=0}^{n-1} (1 - \alpha_{k+1}) \left[ \prod_{l=k+2}^{n+1} \alpha_l \right] \mathscr{G}_k \right] + (1 - \alpha_{n+1}) \mathscr{G}_n \\
&= \sum_{k=0}^{n} (1 - \alpha_{k+1}) \left[ \prod_{l=k+2}^{n+1} \alpha_l \right] \mathscr{G}_k = \sum_{k=0}^{n} a_{n+1,k} \mathscr{G}_k.
\end{split} \tag{6.201}
$$

因此，归纳法证明了第 **(i)** 项。此外，观察可知，(6.196) 和 (6.199) 表明对于所有 $n \in \mathbb{N}$，都有 $m_0 = 0$ 且

$$
\begin{aligned}
m_{n} &= \sum_{k=0}^{n-1} a_{n,k} = \sum_{k=0}^{n-1} (1-\alpha_{k+1}) \left[ \prod_{l=k+2}^{n} \alpha_{l} \right] \\
&= 1 - \alpha_{n} + \sum_{k=0}^{n-2} (1-\alpha_{k+1}) \left[ \prod_{l=k+2}^{n} \alpha_{l} \right] \\
&= 1-\alpha_{n} + \sum_{k=0}^{n-2} (1-\alpha_{k+1}) \left[ \prod_{l=k+2}^{n} \alpha_{l} \right] \\
&= 1-\alpha_{n} + \alpha_{n} \sum_{k=0}^{n-2} a_{n-1,k} = 1-\alpha_{n} + \alpha_{n} m_{n-1}.
\end{aligned}
$$

结合引理 6.3.2，这意味着对于所有 $n \in \mathbb{N}_{0}$，都有

$$
m_{n} = 1 - \prod_{k=1}^{n} \alpha_{k}.
$$

这确立了第 **(ii)** 项。因此，引理 6.3.3 的证明完毕。

## 推论 6.3.4（关于动量梯度下降优化方法的表示）

设 $d \in \mathbb{N}$，$(\gamma_n)_{n \in \mathbb{N}} \subseteq [0, \infty)$，$(a_n)_{n \in \mathbb{N}} \subseteq [0, 1]$，$(a_{n,k})_{(n,k) \in \mathbb{N}_0^2} \subseteq \mathbb{R}$，$\xi \in \mathbb{R}^d$ 满足对于所有 $n \in \mathbb{N}$，$k \in \{0, 1, \ldots, n-1\}$ 有

$$
a_{n,k} = (1-\alpha_{k+1}) \left[ \prod_{l=k+2}^{n} \alpha_{l} \right] \tag{6.204}
$$

令 $\mathcal{L}: \mathbb{R}^d \rightarrow \mathbb{R}$ 和 $\mathcal{G}: \mathbb{R}^d \rightarrow \mathbb{R}^d$ 满足对于所有 $U \in \{V \subseteq \mathbb{R}^d: V \text{ 是开集}\}$，$\theta \in U$ 且 $\mathcal{L}|_U \in C^1(U, \mathbb{R}^d)$，有

$$
\mathcal{G}(\theta) = (\nabla \mathcal{L})(\theta) \tag{6.205}
$$

并设 $\Theta$ 是目标函数 $\mathcal{L}$ 具有广义梯度 $\mathcal{G}$、学习率 $(\gamma_n)_{n \in \mathbb{N}}$、动量衰减因子 $(\alpha_n)_{n \in \mathbb{N}}$ 和初始值 $\xi$ 的动量 GD 过程（参见定义 6.3.1）。则

- (i) 对于所有 $n \in \mathbb{N}$，$k \in \{0, 1, \ldots, n-1\}$，有 $0 \leq a_{n,k} \leq 1$，
- (ii) 对于所有 $n \in \mathbb{N}_0$，有

$$
\sum_{k=0}^{n-1} a_{n,k} = 1 - \prod_{k=1}^{n} \alpha_{k} \tag{6.206}
$$

- 并且
- (iii) 对于所有 $n \in \mathbb{N}$，有

$$
\Theta_{n} = \Theta_{n-1} - \gamma_{n} \left[ \sum_{k=0}^{n-1} a_{n,k} \mathcal{G}(\Theta_{k}) \right]. \tag{6.207}
$$

### 推论 6.3.4 的证明

在整个证明过程中，设 $\mathbf{m}\colon\mathbb{N}_{0}\to\mathbb{R}^{\mathfrak{d}}$ 满足对于所有 $n\in\mathbb{N}$ 有

$$
\mathbf{m}_{0}=0\quad\text{且}\quad\mathbf{m}_{n}=\alpha_{n}\mathbf{m}_{n-1}+(1-\alpha_{n})\mathcal{G}(\Theta_{n-1}). \tag{6.208}
$$

注意 (6.204) 蕴含了第 (i) 项。观察可知，(6.204)、(6.208) 和引理 6.3.3 保证了对于所有 $n\in\mathbb{N}_{0}$，都有

$$
\mathbf{m}_{n}=\sum_{k=0}^{n-1}a_{n,k}\mathcal{G}(\Theta_{k})\quad\text{且}\quad\sum_{k=0}^{n-1}a_{n,k}=1-\prod_{k=1}^{n}\alpha_{k}. \tag{6.209}
$$

这证明了第 (ii) 项。注意 (6.189)、(6.190)、(6.191)、(6.208) 和 (6.209) 表明对于所有 $n\in\mathbb{N}$，都有

$$
\Theta_{n}=\Theta_{n-1}-\gamma_{n}\mathbf{m}_{n}=\Theta_{n-1}-\gamma_{n}\Big[\sum_{k=0}^{n-1}a_{n,k}\mathcal{G}(\Theta_{k})\Big]. \tag{6.210}
$$

这确立了第 (iii) 项。因此，推论 6.3.4 的证明完毕。 $\square$

## 6.3.2 带偏置校正的动量 GD 优化

### 定义 6.3.5（偏置校正动量 GD 优化方法）

设 $\mathfrak{d}\in\mathbb{N}$，$(\gamma_{n})_{n\in\mathbb{N}}\subseteq[0,\infty)$，$(\alpha_{n})_{n\in\mathbb{N}}\subseteq[0,1]$，$\boldsymbol{\xi}\in\mathbb{R}^{\mathfrak{d}}$ 满足 $\alpha_{1}<1$，且设 $\mathcal{L}\colon\mathbb{R}^{\mathfrak{d}}\to\mathbb{R}$ 和 $\mathcal{G}\colon\mathbb{R}^{\mathfrak{d}}\to\mathbb{R}^{\mathfrak{d}}$ 满足对于所有 $U\in\{V\subseteq\mathbb{R}^{\mathfrak{d}}:V\text{ 是开集}\}$，$\theta\in U$ 且 $\mathcal{L}\big|_{U}\in C^{1}(U,\mathbb{R}^{\mathfrak{d}})$，有

$$
\mathcal{G}(\theta)=(\nabla\mathcal{L})(\theta). \tag{6.211}
$$

则我们称 $\Theta$ 是目标函数 $\mathcal{L}$ 具有广义梯度 $\mathcal{G}$、学习率 $(\gamma_{n})_{n\in\mathbb{N}}$、动量衰减因子 $(\alpha_{n})_{n\in\mathbb{N}}$ 和初始值 $\boldsymbol{\xi}$ 的偏置校正动量 GD 过程（我们称 $\Theta$ 是目标函数 $\mathcal{L}$ 具有学习率 $(\gamma_{n})_{n\in\mathbb{N}}$、动量衰减因子 $(\alpha_{n})_{n\in\mathbb{N}}$ 和初始值 $\boldsymbol{\xi}$ 的偏置校正动量 GD 过程）当且仅当 $\Theta\colon\mathbb{N}_{0}\to\mathbb{R}^{\mathfrak{d}}$ 是从 $\mathbb{N}_{0}$ 到 $\mathbb{R}^{\mathfrak{d}}$ 的函数，满足存在 $\mathbf{m}\colon\mathbb{N}_{0}\to\mathbb{R}^{\mathfrak{d}}$ 使得对于所有 $n\in\mathbb{N}$ 有

$$
\Theta_{0}=\boldsymbol{\xi},\quad\quad\mathbf{m}_{0}=0, \tag{6.212}
$$

$$
\mathbf{m}_{n}=\alpha_{n}\mathbf{m}_{n-1}+(1-\alpha_{n})\mathcal{G}(\Theta_{n-1}), \tag{6.213}
$$

且

$$
\Theta_{n}=\Theta_{n-1}-\frac{\gamma_{n}\mathbf{m}_{n}}{1-\prod_{l=1}^{n}\alpha_{l}}. \tag{6.214}
$$

### 推论 6.3.6（关于偏置校正动量 GD 优化方法的表示）

设 $\mathfrak{d}\in\mathbb{N}$，$(\gamma_{n})_{n\in\mathbb{N}}\subseteq[0,\infty)$，$(\alpha_{n})_{n\in\mathbb{N}}\subseteq[0,1]$，$\boldsymbol{\xi}\in\mathbb{R}^{\mathfrak{d}}$，$(a_{n,k})_{(n,k)\in(\mathbb{N}_{0})^{2}}\subseteq\mathbb{R}$ 满足对于所有 $n\in\mathbb{N}$，$k\in\{0,1,\ldots,n-1\}$ 有 $\alpha_{1}<1$ 且

$$
a_{n,k}=\frac{(1-\alpha_{k+1})\prod_{l=k+2}^{n}\alpha_{l}}{1-\prod_{l=1}^{n}\alpha_{l}}, \tag{6.215}
$$

令 $\mathcal{L}: \mathbb{R}^{\mathfrak{d}} \rightarrow \mathbb{R}$ 和 $\mathscr{G}: \mathbb{R}^{\mathfrak{d}} \rightarrow \mathbb{R}^{\mathfrak{d}}$ 满足对于所有 $U \in \{V \subseteq \mathbb{R}^{\mathfrak{d}}: V\text{ 是开集}\}$，$\theta \in U$ 且 $\mathcal{L}\vert_U \in C^1(U, \mathbb{R})$，有

$$
\mathscr{G}(\theta) = (\nabla\mathcal{L})(\theta),
$$

并设 $\Theta$ 是目标函数 $\mathcal{L}$ 具有广义梯度 $\mathscr{G}$、学习率 $(\gamma_n)_{n \in \mathbb{N}}$、动量衰减因子 $(\alpha_n)_{n \in \mathbb{N}}$ 和初始值 $\boldsymbol{\xi}$ 的偏置校正动量 GD 过程（参见定义 6.3.5）。则

- (i) 对于所有 $n \in \mathbb{N}$，$k \in \{0, 1, \ldots, n-1\}$，有 $0 \leq a_{n,k} \leq 1$，
- (ii) 对于所有 $n \in \mathbb{N}$，有

$$
\sum_{k=0}^{n-1}a_{n,k} = 1, \tag{6.217}
$$

- 并且
- (iii) 对于所有 $n \in \mathbb{N}$，有

$$
\Theta_n = \Theta_{n-1} - \gamma_n\left[\sum_{k=0}^{n-1}a_{n,k}\mathscr{G}(\Theta_k)\right]. \tag{6.218}
$$

### 推论 6.3.6 的证明

在整个证明过程中，设 $\mathbf{m}: \mathbb{N}_0 \rightarrow \mathbb{R}^{\mathfrak{d}}$ 满足对于所有 $n \in \mathbb{N}$ 有

$$
\mathbf{m}_0 = 0 \quad \text{且} \quad \mathbf{m}_n = \alpha_n\mathbf{m}_{n-1} + (1-\alpha_n)\mathscr{G}(\Theta_{n-1}) \tag{6.219}
$$

并设 $(b_{n,k})_{(n,k) \in (\mathbb{N}_0)^2} \subseteq \mathbb{R}$ 满足对于所有 $n \in \mathbb{N}$，$k \in \{0, 1, \ldots, n-1\}$ 有

$$
b_{n,k} = (1-\alpha_{k+1})\left[\prod_{l=k+2}^n\alpha_l\right], \tag{6.220}
$$

观察可知 (6.215) 蕴含了第 (i) 项。注意 (6.215)、(6.219)、(6.220) 和引理 6.3.3 保证了对于所有 $n \in \mathbb{N}$，都有

$$
\mathbf{m}_n = \sum_{k=0}^{n-1}b_{n,k}\mathscr{G}(\Theta_k) \quad \text{且} \quad \sum_{k=0}^{n-1}a_{n,k} = \frac{\sum_{k=0}^{n-1}b_{n,k}}{1-\prod_{l=1}^n\alpha_l} = \frac{1-\prod_{l=1}^n\alpha_l}{1-\prod_{l=1}^n\alpha_l} = 1. \tag{6.221}
$$

这证明了第 (ii) 项。观察可知 (6.212)、(6.213)、(6.214)、(6.219) 和 (6.221) 表明对于所有 $n \in \mathbb{N}$，都有

$$
\Theta_n = \Theta_{n-1} - \frac{\gamma_n\mathbf{m}_n}{1-\prod_{l=1}^n\alpha_l} = \Theta_{n-1} - \gamma_n\left[\sum_{k=0}^{n-1}\frac{b_{n,k}}{1-\prod_{l=1}^k\alpha_l}\mathscr{G}(\Theta_k)\right]
$$

$$
= \Theta_{n-1} - \gamma_n\left[\sum_{k=0}^{n-1}a_{n,k}\mathscr{G}(\Theta_k)\right]. \tag{6.222}
$$

这确立了第 (iii) 项。因此，推论 6.3.6 的证明完毕。
