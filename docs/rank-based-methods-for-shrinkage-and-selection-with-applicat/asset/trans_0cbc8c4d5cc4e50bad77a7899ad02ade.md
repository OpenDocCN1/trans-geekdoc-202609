

## 5.2 参数的符号与符号秩估计量

我们考虑参数 \((\theta_j, \beta_j)\)、\(j = 1, ..., p\) 的符号秩统计量。为此，我们采用重参数化：

\((\theta_j, \beta_j) \rightarrow (\theta_j^*, \beta_j^*)\),

其中 \(\theta_j^* = \theta_j + \beta_j \bar{x}_j\) 且 \(\beta_j^* = Q_{n_j}^{-\frac{1}{2}} \beta_j\)，\(Q_{n_j} = \sum_{i=1}^{n_j} (x_{ij} - \bar{x}_j)^2\)。因此，我们有

\(\theta_j + \beta_j x_{n_{ji}} = \theta_j^* + \beta_j^* c_{n_{ji}} \quad \text{for} \quad i = 1, ..., n_j, \qquad (5.2.1)\)

其中

\(c_{n_{ji}} = Q_{n_j}^{-\frac{1}{2}} (x_{n_{ji}} - \bar{x}_j),\)

满足

\(\sum_{i=1}^{n_j} c_{n_{ji}} = 0, \quad \text{and} \quad \sum_{i=1}^{n_j} c_{n_{ji}}^2 = 1.\)

另外，我们用 \(R_{n_{ji}}^+(\theta_j^*, \beta_j^*)\) 表示 \(|y_{n_{ji}} - \theta_j^* - \beta_j^* c_{n_{ji}}|\) 在

\(|y_{n_{ji}} - \theta_j^* - \beta_j^* c_{n_{ji}}|, \quad 1 \le i \le n_j\)

中的秩，其中 \(j = 1, ..., p\)。对于 \((\theta^*, \beta^*) \in \mathbb{R}^2\)，令

\(D_{n_j}(\theta_j^*, \beta_j^*) = \sum_{i=1}^{n_j} |y_{n_{ji}} - \theta_j^* - \beta_j^* c_{n_{ji}}| a_{n_j}^+(R_{n_{ji}}^+(\theta_j^*, \beta_j^*)). \qquad (5.2.2)\)

已知 \(D_{n_j}(\theta_j^*, \beta_j^*)\) 是 \((\theta_j^*, \beta_j^*)\) 的凸、连续分段线性函数，我们定义 \((\hat{\theta}_j^{UR}, \beta_j^{*UR})\) 的 R 估计量为

\((\hat{\theta}_j^{*UR}, \hat{\beta}_j^{*UR}) = \text{argmin}_{(\theta_j^*, \beta_j^*) \in \mathbb{R}^2} \{ D_{n_j}(\theta_j^*, \beta_j^*) \}. \qquad (5.2.3)\)

显然，在 \(D_{n_j}(\theta_j^*, \beta_j^*)\) 的连续点处，我们有

\(\frac{\partial}{\partial \theta_j^*} D_{n_j}(\theta_j^*, \beta_j^*) = -\sum_{i=1}^{n_j} \text{sgn}(y_{n_{ji}} - \theta_j^* - \beta_j^* c_{n_{ji}}) a_{n_j}^+(R_{n_{ji}}^+(\theta_j^*, \beta_j^*))\)

\(= -\sqrt{n_j} \quad T_{n_j}(\theta_j^*, \beta_j^*) \qquad (5.2.4)\)

且

\(\frac{\partial}{\partial \beta_j^*} D_{n_j}(\theta_j^*, \beta_j^*) = -\sum_{i=1}^{n_j} c_{n_{ji}} \text{sgn}(y_{n_{ji}} - \theta_j^* - \beta_j^* c_{n_{ji}}) a_{n_j}^+(R_{n_{ji}}^+(\theta_j^*, \beta_j^*))\)

\(= -L_{n_j}(\theta_j^*, \beta_j^*). \quad (5.2.5)\)

我们使用以下量来表达 R 估计量的 ADB 和 ADL$_2$-风险，

\[\begin{aligned} A_\phi^2 &= \int_0^1 \phi^2(u)du, \quad & A_\psi^2 = \int_0^1 \psi^2(u)du, \\ \psi(u) &= -\frac{f'_0(F_0^{-1}(u))}{f_0(F_0^{-1}(u))}, \end{aligned}\]

和

\(\gamma(\phi, \psi) = \int_0^1 \psi(u)\phi(u)du.\)

另外，令

\[\begin{aligned} A_{n_j} &= \frac{1}{n_j-1} \sum_{i=1}^{n_j} (a_{n_j}^+(i) - \bar{a}_j^+)^2, \\ \bar{a}_j^+ &= \frac{1}{n_j} \sum_{i=1}^{n_j} a^+(i), \\ A_n^2 &= \sum_{j=1}^p (n_j-1) A_{n_j}^2. \end{aligned}\]

请注意，对于给定的 $x_j$，

\(L_{n_j}(\theta_j^*, \beta_j^*) \searrow \beta_j^* \text{ for } \beta_j^* \in \mathbb{R},\)

且

\(T_{n_j}(\theta_j^*, \beta_j^*) \searrow \theta_j^* \text{ for a fixed } \beta_j^*.\)

在 Eq. (5.1.2) 的模型下，且 $\theta^* = \beta^* = 0$，$T_{n_j}(0, 0)$ 和 $L_{n_j}(0, 0)$ 均关于 $(0, 0)$ 具有对称分布。然后，当 \(n \to \infty$ 时，我们有

\(\begin{pmatrix} T_{n_j}(0, 0) \\ L_{n_j}(0, 0) \end{pmatrix} \xrightarrow{\mathcal{D}} \mathcal{N}_2 \left( \begin{pmatrix} 0 \\ 0 \end{pmatrix}, A_\phi^2 \chi_j^{-1} \begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix} \right). \quad (5.2.6)\)

现在，根据第 3.2.1 节，\((\theta_j^*, \beta_j^*)^\top\) 的 R 估计量由以下给出

\(\hat{\beta}_j^{*\text{UR}} = \frac{1}{2}(\hat{\beta}_j^{*(\text{U})} + \hat{\beta}_j^{*(\text{L})}) \quad (5.2.7)\)

其中

\(\hat{\beta}_j^{*(U)} = \sup\left\{\beta_j^* : L_{n_j}(0, \beta_j^*) > 0\right\}\)

\(\hat{\beta}_j^{*(L)} = \inf\left\{\beta_j^* : L_{n_j}(0, \beta_j^*) < 0\right\}\)

和

\(\hat{\theta}_j^{*UR} = \frac{1}{2}(\hat{\theta}_j^{*(U)} + \hat{\theta}_j^{*(L)})\) (5.2.8)

其中

\(\hat{\theta}_j^{*(U)} = \sup\left\{\theta_j^* : T_{n_j}(\theta_j^*, \hat{\beta}_j^{*UR}) > 0\right\},\)

\(\hat{\theta}_j^{*(L)} = \inf\left\{\theta_j^* : T_{n_j}(\theta_j^*, \hat{\beta}_j^{*UR}) < 0\right\}.\)

利用 Jurečková (1971) 渐近线性性结果，对于固定的 \((\hat{\theta}_j^{*UR}, \hat{\beta}_j^{*UR})^\top \in \mathbb{R}^2$，当 \(n \to \infty$ 时（Hajek et al., 1999, 第 325 页），

\(\left| T_{n_j}(n^{-\frac{1}{2}}\hat{\theta}_j^{*UR}, \hat{\beta}_j^{*UR}) - T_{n_j}(0,0) + \gamma(\phi, \psi)\hat{\theta}_j^{*UR} \right| \xrightarrow{P} 0,\) (5.2.9)

和

\(\left| L_{n_j}(\theta_j^{*UR}, n^{-\frac{1}{2}}\hat{\beta}_j^{*UR}) - L_{n_j}(0,0) + \gamma(\phi, \psi)\hat{\beta}_j^{*UR} \right| \xrightarrow{P} 0.\) (5.2.10)

因此，利用 Jaeckel (1972) 的渐近二次逼近结果，当 \(n \to \infty$ 时，我们有

\[\begin{aligned} D_{n_j}(n^{-\frac{1}{2}}\hat{\theta}_j^{*UR}, n^{-\frac{1}{2}}\hat{\beta}_j^{*UR}) - D_{n_j}(0,0) + \hat{\theta}_j^{*UR}T_{n_j}(0,0) \\ + \hat{\beta}_j^{*UR}L_{n_j}(0,0) + \frac{1}{2}\gamma(\phi, \psi)\left[(\hat{\theta}_j^{*UR})^2 + (\hat{\beta}_j^{*UR})^2\right] \xrightarrow{P} 0. \end{aligned}\]

因此，当 \(n \to \infty$ 时，我们有

\(\begin{pmatrix} \sqrt{n}(\hat{\theta}_j^{*UR} - \theta_j) \\ \sqrt{n}(\hat{\beta}_j^{*UR} - \beta_j) \end{pmatrix} - \gamma^{-1}(\phi, \psi) \begin{pmatrix} T_{n_j}(0,0) \\ L_{n_j}(0,0) \end{pmatrix} \xrightarrow{P} 0.\) (5.2.11)

此外，利用 \((\theta, \beta)^\top$ 的平移和尺度等价性质，我们可以将 \((\theta_j, \beta_j)$ 的估计量写为
\(\hat{\theta}_j^{UR} = \hat{\theta}_j^{*UR} - \hat{\beta}_j^{*UR}\bar{x}_j \text{ and } \hat{\beta}_j^{UR} = Q_{n_j}^{-\frac{1}{2}}\hat{\beta}_j^{*UR},\) (5.2.12)

其中 \(Q_{n_j} = \sum_{i=1}^{n_j}(x_{ji} - \bar{x}_j)^2$，这导致（当 \(n \to \infty$ 时），
\(\begin{pmatrix} \sqrt{n}(\hat{\theta}_j^{\text{UR}} - \theta_j) \\ \sqrt{n}(\hat{\beta}_j^{\text{UR}} - \beta_j) \end{pmatrix} - \gamma^{-1}(\phi, \psi) \begin{pmatrix} 1 & -\frac{\sqrt{n}\bar{x}_j}{Q_{n_j}} \\ 0 & 1 \end{pmatrix} \begin{pmatrix} T_{n_j}(0, 0) \\ L_{n_j}(0, 0) \end{pmatrix} \xrightarrow{P} 0.\)

接着，我们有如下定理 5.1。

## 定理 5.1 在局部替代类下

\(K_{(n)} : \beta_{(n)} = n^{-\frac{1}{2}} \delta = n^{-\frac{1}{2}} (\delta_1^\top, \delta_2^\top)^\top\)

并假设 Eq. (5.1.2) 模型在 \(n \to \infty$ 时满足常规条件，对于 \(\hat{\theta}^{\text{UR}} = (\hat{\theta}_1^{\text{UR}}, ..., \hat{\theta}_p^{\text{UR}})^\top\) 和 \(\hat{\beta}^{\text{UR}} = (\hat{\beta}_1^{\text{UR}}, ..., \hat{\beta}_p^{\text{UR}})^\top\)，我们有以下结果：

\(\begin{pmatrix} \sqrt{n}(\hat{\theta}^{\text{UR}} - \theta) \\ \sqrt{n}(\hat{\beta}^{\text{UR}} - \beta) \end{pmatrix} \overset{\mathcal{D}}{\to} \mathcal{N}_{2p} \left( \begin{pmatrix} 0 \\ 0 \end{pmatrix}, \eta^2 \begin{pmatrix} \mathcal{K}^{-1} + T_0 D_{22} T_0 & -T_0 D_{22} \\ -T_0 D_{22} & D_{22} \end{pmatrix} \right)\)

其中

\(D_{22}^{-1} = \text{Diag}(\chi_j Q_j | j = 1, ..., p),\)

\(D_{11} = \mathcal{K}^{-1} + T_0 D_{22} T_0\)

和

\(T_0 = \text{Diag}(\bar{x}_1, ..., \bar{x}_p).\)

对于对 \(\beta$ 的子假设进行检验，我们可以考虑假设 \(\beta_2 = 0\)，其中 \(\beta = (\beta_1^\top, \beta_2^\top)^\top\)。我们可以使用由以下定义的统计量 \(\mathcal{L}_n\)

\(\mathcal{L}_n = A_{n(2)}^{-2} L_{n(2)}^{\top}(0) D_{22}^{[2]} L_{n(2)}(0),\)

其中 \(L_{n(2)}(0) = L_{n(2)}(\hat{\beta}_{1n_1}^{\text{UR}}, 0)\) 是 \(p_2$-维检验统计量，

\(D_{22} = \text{Diag}(D_{22}^{[1]}, D_{22}^{[2]}),\)

\(A_n^2 = (A_{n(1)}^2, A_{n(2)}^2)$ 分别具有 \(p_1$ 和 \(p_2$ 维度。因此，在 \(\mathcal{H}_0 : \beta_2 = 0\) 下，当 \(n \to \infty$ 时，\(\mathcal{L}_n\) 服从 \(\chi^2_{p_2}\)；而在局部替代 \(K_{(n)} : \beta_{2(n)} = n^{-\frac{1}{2}} \delta_2$、\(\delta_2 = (\delta_{21}, ..., \delta_{2p_2})^\top\) 下，\(\mathcal{L}_n\) 服从具有 \(p_2$

