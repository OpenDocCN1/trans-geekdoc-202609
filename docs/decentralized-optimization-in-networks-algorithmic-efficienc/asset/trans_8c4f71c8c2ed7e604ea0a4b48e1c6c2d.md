

## 算法 1 ET-DSGT：事件触发去中心化随机梯度追踪算法。

**初始化：** 每个代理 \( i \in \mathcal{V} \) 初始化 \( x_{t_0}^i = x_0^i \in \mathbb{R}^d \) 和 \( y_{t_0}^i = y_0^i = \nabla g(x_{t_0}^i, s_0^i) \in \mathbb{R}^d \)。

**本地更新：** 每个代理 \( i \in \mathcal{V} \) 对 \( j \in \mathcal{N}_i \) 重复执行

- 1: 对于所有 \( t = 0, 1, \cdots \) 执行
- 2: 按以下方式更新估计器 \( x_{t+1}^i \)：
  \[
  x_{t+1}^i = x_t^i + \sum_{j=1}^N w^{ij}(x_{t_k^j}^j - x_{t_k^i}^i) - \alpha_t y_t^i, \quad (4.5a)
  \]
  其中 \( w^{ij} \) 是代理 \( i \) 与其邻居 \( j \) 之间的权重，衰减步长 \( \alpha_t = a/(t+1), a > 0 \)。
- 3: 按以下方式更新 \( y_{t+1}^i \)：
  \[
  y_{t+1}^i = y_t^i + \sum_{j=1}^N w^{ij}(y_{t_k^j}^j - y_{t_k^i}^i) + \nabla g^i(x_{t+1}^i, S_{t+1}^i) - \nabla g^i(x_t^i, S_t^i), \quad (4.5b)
  \]
  其中 \( S_0^i, S_1^i, \dots \) 是 \( S^i \) 的独立同分布样本。
- 4: 在 (4.4) 中测量 \( e_t^{i,x}, e_t^{i,y} \)，然后检查 (4.3) 是否满足。
- 5: **如果** (4.3) 满足 **则**
- 6: 将 \( x_{t+1}^i \) 和 \( y_{t+1}^i \) 广播到 \( j \in \mathcal{N}^i \)，并刷新触发时间。
- 7: **否则**
- 8: 代理 \( j \) 保持本地估计器不变。
- 9: **结束如果**
- 10: **结束循环**

传输其实时状态估计器 \( x_{t+1}^i \) 和 \( y_{t+1}^i \)，即使在计算完成后也是如此。换句话说，代理 \( i \) 在没有任何修改的情况下维护其本地估计器。因此，通过实施事件触发机制，ET-DSGT 算法规避了对持续实时通信的需求。

根据 (4.4) 和假设 4.2，算法 1 中的迭代更新步骤可以如下表述：

\[
x_{t+1}^i = \sum_{j=1}^N w^{ij} x_t^j + \hat{e}_t^{i,x} - \alpha_t y_t^i, \quad (4.6a)
\]

\[
y_{t+1}^i = \sum_{j=1}^N w^{ij} y_t^j + \hat{e}_t^{i,y} + \nabla g_{t+1}^i - \nabla g_t^i, \quad (4.6b)
\]

其中 \(\hat{e}_t^{i,x} = \sum_{j=1}^N w^{ij}(e_t^{j,x} - \hat{e}_t^{i,x})\) 和 \(\hat{e}_t^{i,y} = \sum_{j=1}^N w^{ij}(e_t^{j,y} - \hat{e}_t^{i,y})\)。

出于分析目的，我们定义以下记号：\(x_t = [(x_t^1)^\mathrm{T}, ..., (x_t^N)^\mathrm{T}]^\mathrm{T}\)，\(y_t = [(y_t^1)^\mathrm{T}, ..., (y_t^N)^\mathrm{T}]^\mathrm{T}\)，\(\hat{e}_t^x = [(\hat{e}_t^{1,x})^\mathrm{T}, ..., (\hat{e}_t^{N,x})^\mathrm{T}]^\mathrm{T}\)，\(\hat{e}_t^y = [(\hat{e}_t^{1,y})^\mathrm{T}, ..., (\hat{e}_t^{N,y})^\mathrm{T}]^\mathrm{T}\)，\(\nabla G_t = [(\nabla g_t^1)^\mathrm{T}, ..., (\nabla g_t^N)^\mathrm{T}]^\mathrm{T}\)，以及 \(\hat{W} = W \otimes I_d\)。随后，算法 1 可以以简洁的方式表示如下：

\[
x_{t+1} = \hat{W} x_t + \hat{e}_t^x - \alpha_t y_t, \quad (4.7a)
\]
\[
y_{t+1} = \hat{W} y_t + \hat{e}_t^y + \nabla G_{t+1} - \nabla G_t. \quad (4.7b)
\]

**注释 4.3.** 与参考文献 [38–41] 中引用的现有去中心化事件触发技术以及参考文献 [14,16,17,36] 中提到的去中心化随机梯度追踪方法相比，算法 1 成功实现了两个目标。具体来说，算法 1 在提高通信效率的同时也确保了精确收敛。因此可以推断，本章提出了一种独特的去中心化优化算法。

## 4.3 收敛保证

在本节中，我们从均方收敛角度考察 ET-DSGT 的收敛特性。

### 4.3.1 初步结果

出于分析目的，我们引入两个支持序列，分别记为 \(\{y'_t\}\) 和 \(\{\xi_t\}\)，定义如下：

\[
y'_{t+1} = \hat{W} y'_t + \nabla F_{t+1} - \nabla F_t, \quad y'_0 = \nabla F_0, \quad (4.8)
\]
\[
\xi_{t+1} = \hat{W} \xi_t + \hat{e}_t^y + \varepsilon_{t+1} - \varepsilon_t, \quad \xi_0 = \varepsilon_0, \quad (4.9)
\]

其中 \(\varepsilon_t^i := \nabla g^i(x_t^i, \zeta_t^i) - \nabla f^i(x_t^i)\)，\(\varepsilon_t = \nabla G_t - \nabla F_t\)，且 \(\nabla F_t = [\nabla f^1(x_t^1)^\mathrm{T}, ..., \nabla f^N(x_t^N)^\mathrm{T}]^\mathrm{T}\)。此外，我们确立以下定义：

\[
\bar{x}_t = (\frac{1}{N} \mathbf{1}_N^\mathrm{T} \otimes I_d) x_t, \quad \bar{y}'_t = (\frac{1}{N} \mathbf{1}_N^\mathrm{T} \otimes I_d) y'_t.
\]

随后，回顾 (4.4) 和假设 4.2(ii)，可以清楚地推断出以下结论：

\[
\frac{1}{N} (\mathbf{1}_N^\mathrm{T} \otimes I_d) \hat{e}_t^x = 0, \quad \frac{1}{N} (\mathbf{1}_N^\mathrm{T} \otimes I_d) \hat{e}_t^y = 0, \quad \forall t \ge 0.
\]

此外，我们重新审视在 [34] 中引入的矩阵范数 \(||\cdot||\)。该范数具有以下特性：

\[
\tau_w := ||\hat{W} - \frac{1}{N} \mathbf{1}_N \mathbf{1}_N^\mathrm{T} \otimes I_d|| < 1. \quad (4.10)
\]

在推导补充结果之前，我们在引理 4.1 中提出一个有用的推论，其证明可见参考文献 [14]。

**引理 4.1.** 存在一个正常数 \(c_\rho\)，使得不等式 \(\sum_{l=0}^{t-1} \tau_w^{t-l} \alpha_l \le c_\rho \alpha_t\) 成立，其中 \(\tau_w\) 在 (4.10) 中定义。

此外，在引理 4.2 中，我们提出了最初在 [43] 中建议的引理 4.3 的扩展。该引理的证明可在 [43] 中查阅。

**引理 4.2.** 假设正序列 \(\{\gamma_t\}\)、\(\{\rho_t\}\)、\(\{\varphi_t\}\) 满足以下标准：

- (i) 序列 \(\{\gamma_t\}\) 和 \(\{\rho_t\}\) 包含 0 到 1 之间的值，满足 \(\sum_{t=0}^\infty \gamma_t^2 < \infty\) 和 \(\rho_t < 1\)，

- (ii) \(\limsup_{t \to \infty} (\gamma_t \sqrt{\varphi_t} + \varphi_{t-1}/\varphi_t) < \infty\)，\(\sum_{t=0}^\infty \varphi_t^{-1} < \infty\) 且 \(\liminf_{t \to \infty} (\gamma_t \sqrt{\varphi_t})^{-1} (\varphi_{t-1}/\varphi_t - \rho_t) > 0\)。

在标量 \(M > 0\) 和 \(0 < p < 1\) 的前提下，序列 \(u_t\) 和 \(v_t\) 满足 \(t \ge t_0\) 的条件，

\[
\begin{aligned} u_{t+1} \le & \rho_t u_t + M \gamma_t \sqrt{u_t(1+u_t+v_t)} \\ & + M \gamma_t (\gamma_t + \sum_{l=0}^t \gamma_l p^{t-l} u_l + \sum_{l=0}^t \gamma_l p^{t-l} v_l), \end{aligned} \quad (4.11)
\]

\[
\begin{aligned} v_{t+1} \le & v_t + M u_t + M \gamma_t \sqrt{u_t(1+u_t+v_t)} \\ & + M \gamma_t (\gamma_t + \sum_{l=0}^t \gamma_l p^{t-l} u_l + \sum_{l=0}^t \gamma_l p^{t-l} v_l), \end{aligned} \quad (4.12)
\]

则

\[
\sup_t v_t < \infty, \quad \limsup_{t \to \infty} \varphi_t u_t < \infty.
\]

### 4.3.2 辅助结果

在本小节中，提出了若干支持结果，使得主要结论能够清晰地概述。

**引理 4.3.** 假设假设 4.1–4.3 有效。因此，我们可以推断出

\[
\sup_t \mathbb{E}[||\xi_t||^2] \le \frac{2 c_w N}{(1-\tau_w)^2} (\frac{C \pi^2}{6} + U_1). \quad (4.13)
\]

_证明._ 基于序列 \(\{\xi_t\}\) 的定义，我们可以推断

\[
\xi_t = \sum_{l=0}^{t-1} \hat{W}(t, l) e_l^\gamma + \sum_{l=0}^t \hat{W}(t, l) \varepsilon_l,
\]

其中

\[
\hat{W}(t, l) := \hat{W}^{t-l-1}(\hat{W} - I_{Nd})(l < t),
\]
\[
\hat{W}(t, t-1) := \hat{W} - I_{Nd}, \hat{W}(t, t) := I_{Nd}.
\]

随后，得到

\[
\mathbb{E}[||\xi_t||^2] \le 2 \sum_{l_1=0}^{t-1} \sum_{l_2=0}^{t-1} ||\hat{W}(t, l_1)|| ||\hat{W}(t, l_2)|| \mathbb{E}[||e_{l_1}^y|| ||e_{l_2}^y||] + 2 \sum_{l_3=0}^{t} \sum_{l_4=0}^{t} ||\hat{W}(t, l_3)|| ||\hat{W}(t, l_4)|| \mathbb{E}[||\epsilon_{l_3}|| ||\epsilon_{l_4}||].
\]

根据假设 4.2，我们得到

\[
||\hat{W}^t(\hat{W} - I_{Nd})|| = ||(\hat{W} - \frac{1_N 1_N^T}{N} \otimes I_d)\hat{W}^{t-1}(\hat{W} - I_{Nd})|| \le \tau_w ||\hat{W}^{t-1}(\hat{W} - I_{Nd})|| \le \cdots \le \tau_w^t ||\hat{W} - I_{Nd}||,
\]

其中 \(\tau_w\) 在 (4.10) 中定义。记 \(c_w := \max\{1, ||\hat{W} - I_{Nd}||^2/\tau_w^2\}\)。在此基础上，我们可以进一步推导

\[
\mathbb{E}[||\xi_t||^2] \le 2c_w \sum_{l_1=0}^{t-1} \sum_{l_2=0}^{t-1} \tau_w^{2t-l_1-l_2} \mathbb{E}[||e_{l_1}^y|| ||e_{l_2}^y||] + 2c_w \sum_{l_3=0}^{t} \sum_{l_4=0}^{t} \tau_w^{2t-l_3-l_4} \mathbb{E}[||\epsilon_{l_3}|| ||\epsilon_{l_4}||] \le 2c_w \sum_{l_1=0}^{t-1} \tau_w^{t-l_1} \sum_{l_2=0}^{t-1} \tau_w^{t-l_2} \mathbb{E}[\frac{||e_{l_1}^y||^2 + ||e_{l_2}^y||^2}{2}] + 2c_w \sum_{l_3=0}^{t} \tau_w^{t-l_3} \sum_{l_4=0}^{t} \tau_w^{t-l_4} \mathbb{E}[\frac{||\epsilon_{l_3}||^2 + ||\epsilon_{l_4}||^2}{2}] \le \frac{2c_w N}{(1-\tau_w)^2}(\frac{C\pi^2}{6} + U_1),
\]

其中最后一个不等式是根据假设 4.3(ii)、条件 \(\tau_w < 1\) 以及观察 \(||e_t^{i,y}||^2 \le C/(t+1)^2\) 推导出来的。因此，(4.13) 成立。\(\square\)

**引理 4.4.** 序列 \(\{y_t\}, \forall t \ge 1,\) 由以下不等式上界：

\[
\mathbb{E}[||\xi_t||^2] \le 4\mathbb{E}[||y'_t - 1_N \otimes \bar{y}'_t||^2] + 4L^2\mathbb{E}[||x_t - 1_N \otimes \bar{x}_t||^2] + \frac{4L^2}{N}\mathbb{E}[||\bar{x}_t - x^*||^2] + \frac{8c_w N}{(1-\tau_w)^2}(\frac{C\pi^2}{6} + U_1).
\]

