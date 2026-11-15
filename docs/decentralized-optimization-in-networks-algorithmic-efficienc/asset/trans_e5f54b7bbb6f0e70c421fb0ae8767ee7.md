

## 算法 2 基于每个节点随机睡眠协议的去中心化异步算法 $i \in \mathcal{V}$。

- **1. 初始化:** 每个节点 $i$ 初始化 $x_i^0 \in \mathbb{R}$、$y_i^0 \in \mathbb{R}$、$k_i^0 \in \mathbb{R}^n$、$v_i^0 = y_i^0$ 和 $u_i^0 = k_i^0$。
- **2.** 对于 $t = 0, 1, 2, \dots$ 执行
- **3. 生成随机变量:** 独立同分布地生成一个伯努利随机变量 $h_i^t$。
- **4. 对偶变量共识:** 按以下方式更新两个中间状态变量 $v_i^t, u_i^t$:

\(\left\{\begin{array}{ l } h_i^t = 1: v_i^t = \sum_{j=1}^n \hat{w}_{ij}^t y_j^t, u_i^t = \sum_{j=1}^n \hat{w}_{ij}^t k_j^t, \\ h_i^t = 0: v_i^t = y_i^t, u_i^t = k_i^t, \end{array}\right. \quad (1.41)\)

其中 $\hat{w}_{ij}^t$ 是时刻 $t$ 从节点 $j$ 到节点 $i$ 的权重。

- **5. 原始变量优化:** 按以下方式更新局部原始变量 $x_i^t$:

\(x_i^{t+1} = \arg\min_{x_i \in \Omega_i} C_i(x_i) - v_i^t(x_i - r_i).\)

- **6. 对偶变量优化:** 按以下方式更新 $y_i^t, k_i^t$:

\(\left\{\begin{array}{ l } h_i^t = 1: \\ \quad z_i^t = u_i^t - \alpha_i^t 1_n, \\ \quad y_i^{t+1} = v_i^t - \frac{[J_i(v_i^t) - \xi_i^t] z_{i+}^t}{1+||a_i^t||^2} a_i^t, \\ \quad k_i^{t+1} = z_i^t + \frac{[J_i(v_i^t) - \xi_i^t] z_{i+}^t}{1+||a_i^t||^2} e_i, \\ h_i^t = 0: y_i^{t+1} = y_i^t, k_i^{k+1} = k_i^t, \end{array}\right. \quad (1.42)\)

其中 $\alpha_i^t$ 是步长，向量 $a_i^t \in \partial J_i(v_i^t)$。

- **7. 结束循环**

并且 $\hat{w}_{ii}^t = 1 - \sum_{j \in \mathcal{N}_i^{\text{in}}, j \neq i} \hat{w}_{ij}^t > \rho, \forall i \in \mathcal{V}$，其中 $0 < \rho < 1$。显而易见，每个矩阵 $\hat{W}^t, t \ge 0$ 都具有行随机性质。为提高可读性并简化记号，设计用于求解公式 (1.16) 的算法 (1.41) 和 (1.42) 可按以下两种情况表示:

\(p_i^{t+1} = h_i^t - \frac{[f_i(h_i^t)]_+ \xi_i^t}{||\xi_i^t||^2}, \quad h_i^t = 1, \quad (1.43a)\)

\(p_i^{t+1} = \sum_{j=1}^n \hat{w}_{ij}^t p_j^t, \quad h_i^t = 0, \quad (1.43b)\)

∀i ∈ V, t ≥ 0，其中对于 $h_i^t = 1$，有 $h_i^t = \sum_{j=1}^n \hat{w}_{ij}^t p_j^t - \alpha_i^t b$。此外，若 $[f_i(h_i^t)]_+ > 0$，则向量 $\xi_i^t \in \partial[f_i(h_i^t)]_+$；若 $[f_i(h_i^t)]_+ = 0$，则对某个 $\xi_i \neq 0_{n+1}$ 有 $\xi_i^t = \xi_i$。

## 1.5.2 算法 2 的收敛性分析

在本小节中，我们深入探讨算法 2 的收敛性。为后续分析奠定基础，我们引入一个关键的引理，它作为支持我们主要结论的核心要素。

**引理 1.6.** [32] 在假设 1.3 成立的前提下，我们考虑加权矩阵 $\hat{W}^t$。对于任意 $t \ge s$，我们定义乘积矩阵 $\hat{W}^{t:s}$ 为从 $\hat{W}^{t-1}$ 到 $\hat{W}^s$ 的矩阵连续乘积，并约定 $\hat{W}^{s:s}$ 为单位矩阵 $I_n$。$\hat{W}^{t:s}$ 的元素记为 $\hat{w}_{ij}^{t:s}$。此外，存在一个归一化向量 $\pi^t$，满足 $(\pi^t)^T 1_n = 1$，使得对所有 $t \ge 0$,

- (i) 存在常数 $H > 0$ 和 $0 < \lambda < 1$，使得对属于集合 $\mathcal{V}$ 的任意一对索引 $i, j$ 以及所有 $t \ge s$，$\hat{w}_{ij}^{t:s}$ 与 $\pi_j^s$ 的绝对差均由 $H(\lambda)^{t-s}$ 界定。
- (ii) 存在常数 $\varrho \ge (\rho)^{(n-1)B}$，使得对任何 $i \in \mathcal{V}$ 和 $t \ge 0$，都有 $\pi_i^t \ge \varrho$。
- (iii) $(\pi^{t'})^T = (\pi^{t+1})^T \hat{W}^t$。

在接下来的引理中，我们建立一个与第 1.4 节中引理 1.5 类似的可比关系。该关系将作为推导后续分析中主要结论的基础。

**引理 1.7.** 假设假设 1.1 和 1.3 成立，我们可以断言：对于任意给定的满足 $0 < \epsilon < 1/2$ 的 $\epsilon$，存在一个阈值 $\hat{t} = \hat{t}(\epsilon, n)$（足够大），使得对于所有大于等于 $\hat{t}$ 的时刻索引 $t$、属于集合 $S_0$ 的任意元素 $v$ 以及来自集合 $\mathcal{V}$ 的任意节点 $i$，

\[
\sum_{i=1}^n \pi_i^{t+1} \mathbb{E}_t \left[ || p_i^{t+1} - v ||^2 \right]
\le (1 + \alpha_3 / t^{3/2-\epsilon}) \sum_{i=1}^n \pi_i^t || p_i^t - v ||^2 - \hat{\eta}_{\min} \beta \sum_{i=1}^n \pi_i^{t+1} || \phi_i^t - \phi_i^t ||^2
- \frac{2}{t} b^T (\bar{\phi}^t - v) + \left[ \frac{\alpha_3}{t^{3/2-\epsilon}} + \alpha_2(1 + 4v + \tau) / t^2 \right] ||b||^2,
\]

其中 $\bar{\phi}^t = \sum_{i=1}^n \pi_i^{t+1} \phi_i^t$，$\tau > 1$，$v > \delta\tau D^2 / 4(\tau-1)$，且对于某个 $\delta > 0$，有 $\beta = (\tau-1)/(\delta\tau D^2) - 1/4v > 0$。

**证明.** (i) $h_i^t = 1$: 借鉴引理 1.5 的证明，我们可以推断，对于任何节点 $i \in \mathcal{V}$，

\[
||p_i^{t+1} - v||^2 + \beta||\phi_i^t - \phi_i^t||^2
\le (1 + \frac{\alpha_3}{t^{3/2-\epsilon}}) \sum_{j=1}^n \hat{w}_{ij}^t ||p_j^t - v||^2 - \frac{2}{t\eta_i} b^T(\phi_i^t - v)
+ \frac{\alpha_3||b||^2}{t^{3/2-\epsilon}} + \frac{\alpha_2(1 + 4v + \tau)||b||^2}{t^2}, \quad (1.44)
\]

其中 $\beta$ 的定义为 $\beta = \frac{\tau-1}{\delta\tau D^2} - \frac{1}{4v}$，其中 $\tau$ 和 $v$ 是可调因子。在此，我们假设 $v > \frac{\delta\tau D^2}{4(\tau-1)}$ 且 $\tau > 1$，这两点均确保 $\beta > 0$。

(ii) $h_i^t = 0$: 对于任何 $i \in \mathcal{V}$，由 (1.43b) 可知，对于任何 $v \in \Xi_0$，

\[
||p_i^{t+1} - v||^2 = ||\sum_{j=1}^n \hat{w}_{ij}^t p_j^t - v||^2
\le (1 + \frac{\alpha_3}{t^{3/2-\epsilon}}) \sum_{j=1}^n \hat{w}_{ij}^t ||p_j^t - v||^2. \quad (1.45)
\]

通过整合公式 (1.44) 和 (1.45) 的结果，并对 $\mathcal{F}^t$ 施加条件期望，我们得到以下结论:

\[
\mathbb{E}_t [||p_i^{t+1} - v||^2]
\le (1 + \frac{\alpha_3}{t^{3/2-\epsilon}}) \sum_{j=1}^n \hat{w}_{ij}^t ||p_j^t - v||^2 - \frac{2}{t} b^T(\phi_i^t - v) + \frac{\alpha_3||b||^2}{t^{3/2-\epsilon}}
- \eta_i \beta ||\phi_i^t - \phi_i^t||^2 + \frac{\alpha_2(1 + 4v + \tau)||b||^2}{t^2}. \quad (1.46)
\]

通过将公式 (1.46) 两边乘以 $\pi_i^{t+1}$ 并对从 1 到 $n$ 的所有 $i$ 求和得到的表达式求和，我们得到以下关系:

\[
\sum_{i=1}^n \pi_i^{t+1} \mathbb{E}_t [||p_i^{t+1} - v||^2]
\le (1 + \frac{\alpha_3}{t^{3/2-\epsilon}}) \sum_{i=1}^n \pi_i^{t+1} \sum_{j=1}^n \hat{w}_{ij}^t ||p_j^t - v||^2
- \hat{\eta}_{\min}\beta \sum_{i=1}^n \pi_i^{t+1} ||\phi_i^t - \phi_i^t||^2 - \frac{2}{t} \sum_{i=1}^n \pi_i^{t+1} b^T(\phi_i^t - v)
+ \left[ \frac{\alpha_3}{t^{3/2-\epsilon}} + \frac{\alpha_2(1 + 4v + \tau)}{t^2} \right] ||b||^2. \quad (1.47)
\]

利用引理 1.6 (iii) 中所述的恒等式 $(\pi^t)^\mathrm{T} = (\pi^{t+1})^\mathrm{T} \hat{W}^t$，只需证明

\[
\sum_{i=1}^n \pi_i^{t+1} \sum_{j=1}^n \hat{w}_{ij}^t || p_j^t - v ||^2 = \sum_{j=1}^n || p_j^t - v ||^2 \sum_{i=1}^n \pi_i^{t+1} \hat{w}_{ij}^t
= \sum_{i=1}^n \pi_i^t || p_i^t - v ||^2 . \quad (1.48)
\]

令 $\tilde{\phi}^t$ 表示使用概率 $\pi^{t+1}$ 对 $z^t$ 进行加权求和: $\tilde{\phi}^t = (\pi^{t+1})^\mathrm{T} z^t = \sum_{i=1}^n \pi_i^{t+1} \phi_i^t$。然后，我们可以建立关系 $\sum_{i=1}^n \pi_i^{t+1} b^\mathrm{T} (\phi_i^t - v) = b^\mathrm{T} (\tilde{\phi}^t - v)$。将此结果与公式 (1.47) 和 (1.48) 结合，我们可以直接得出引理 1.7 中所述的结论，从而完成证明。$\square$

接下来，我们利用引理 1.7 提出的研究结果，推导算法 2 的关键结果。

**定理 1.2.** 鉴于算法 2，在假设 1.1 和 1.3 成立的前提下，对于任意满足 $0 < \varepsilon < 1/2$ 的 $\varepsilon$，存在一个阈值 $\hat{t} = \hat{t}(\varepsilon, n)$（足够大），使得对所有 $t \ge \hat{t}$ 和 $i \in \mathcal{V}$，概率 $p_i^t$ 几乎必然收敛到 $p^*$ 且变量 $x_i^t$ 几乎必然收敛到 $x_i^*$。

_证明._ 通过在引理 1.7 中将 $v$ 设为 $p^*$，我们立即得到以下结果:

\[
\sum_{i=1}^n \pi_i^{t+1} \mathbb{E}_t \left[ || p_i^{t+1} - p^* ||^2 \right]
\le (1 + \frac{\alpha_3}{t^{3/2-\varepsilon}}) \sum_{i=1}^n \pi_i^t || p_i^t - p^* ||^2 - \hat{\eta}_{min}\beta \sum_{i=1}^n \pi_i^{t+1} || \phi_i^t - \phi_i^t ||^2
- \frac{2}{t} b^\mathrm{T} (\tilde{\phi}^t - p^*) + \left[ \frac{\alpha_3}{t^{3/2-\varepsilon}} + \alpha_2(1+4v+\tau) / t^2 \right] ||b||^2 . \quad (1.49)
\]

基于定理 1.1 的证明以及公式 (1.49) 中的各个项，显然引理 1.3 的所有先决条件均已满足。因此，应用引理 1.3 得出结论:

\[
\left\{ \sum_{i=1}^n \pi_i^t || p_i^t - p^* ||^2 \right\} \text{ converges a.s. as } t \to \infty, \quad (1.50a)
\]
\[
\sum_{t=0}^\infty -\frac{2}{t} b^\mathrm{T} (\tilde{\phi}^t - p^*) < \infty \quad a.s. , \quad (1.50b)
\]
\[
\sum_{t=0}^\infty \sum_{i=1}^n \pi_i^{t+1} || \phi_i^t - \phi_i^t ||^2 < \infty \quad a.s. . \quad (1.50c)

