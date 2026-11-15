

我们注意到，$\hat{\theta}_n^{SR+}(\lambda)$ 的 ADL$_2$-risk 在 $\Delta^2 \in \mathbb{R}^+$ 上均优于 Saleh-type R-estimator $\hat{\theta}_n^{SR}(\lambda)$，如表格的第四列和第五列所示。还可注意到，当 $0 < \Delta^2 < 2 \ln(2)$ 时，$\hat{\theta}_n^{SR+}(\lambda)$ 也优于 $\hat{\theta}_n^{UR}$；否则，$\hat{\theta}_n^{UR}$ 优于 $\hat{\theta}_n^{SR+}(\lambda)$。参见表格的第 5 列。

- (g) nEnet-type 与 positive-rule Saleh-type R-estimators 的比较。考虑 $\hat{\theta}_n^{ENetRE}(\lambda, \alpha)$ 与 $\hat{\theta}_n^{SR+}(\lambda)$ 的 ADL$_2$-risk 差值，其由

$$
\eta^2 \left( \rho_{ST}(\lambda \alpha, \Delta) - \frac{1}{[1 + \lambda(1 - \alpha)]^2} \left[ \rho_{ST}(\lambda \alpha, \Delta) + \lambda^2(1 - \alpha)^2 \Delta^2 + 2\lambda(1 - \alpha)\Delta \{ \Delta \mathcal{H}_3(\lambda \alpha, \Delta^2) - \lambda \alpha (\Phi(\lambda \alpha - \Delta) - \Phi(\lambda \alpha + \Delta)) \} \right] \right) = \eta^2 \rho_{ST}(\lambda \alpha, \Delta) \left[ 1 - \frac{1}{[1 + \lambda(1 - \alpha)]^2} \right] - \frac{1}{[1 + \lambda(1 - \alpha)]^2} \left[ \lambda^2(1 - \alpha)^2 \Delta^2 + 2\lambda(1 - \alpha)\Delta \{ \Delta \mathcal{H}_3(\lambda \alpha, \Delta) - \lambda \alpha (\Phi(\lambda \alpha - \Delta) - \Phi(\lambda \alpha + \Delta)) \} \right].
$$

该表达式可能为“正”、“负”或零。因此，positive-rule Saleh 和 nEnetRE 均不在 $\Delta^2$ 上统一主导对方，同样，ridge 和 nEnetRE 也不互相统一主导。这在表格的第 2、5 和 6 列中所示。这些结果是预期的，因为 nEnetRE 是两个 R-estimators 的组合。

## 3.8 简单线性模型

在本节中，我们考虑简单线性模型，

$$
y_i = \theta + \beta x_i + \varepsilon_i, \ i = 1, ..., n \tag{3.8.1}
$$

其中 $\varepsilon_1, ..., \varepsilon_n$ 为具有对称累积分布函数（c.d.f.）$F(\cdot)$ 和概率密度函数（p.d.f.）$f(\cdot)$ 的 i.i.d. 随机变量，且 $f(\cdot)$ 具有有限 Fisher 信息量 $I(f) < \infty$。令 $Q_n = \sum_{i=1}^n (x_i - \bar{x}_n)^2$。我们可以将 (3.8.1) 改写为

$$
y_i = \theta^* + \beta^* Q_n^{-\frac{1}{2}}(x_i - \bar{x}_n) + \varepsilon_i, \ i = 1, ..., n \tag{3.8.2}
$$

其中 $\theta^* = \theta + \beta \bar{x}_n$ 且 $\beta^* = Q_n^{\frac{1}{2}} \beta$。显然，

$$
Q_n^{-\frac{1}{2}} \sum_{i=1}^n (x_i - \bar{x}_n) = 0 \quad \text{and} \quad Q_n^{-1} \sum_{i=1}^n (x_i - \bar{x}_n)^2 = 1.
$$

令 $c_i = Q_n^{-\frac{1}{2}}(x_i - \bar{x}_n), \ i = 1, ..., n$。此外，假设 $R_n^+(\theta^*, \beta^*)$ 是 $|y_i - \theta^* - \beta^* c_i|$ 在 $|y_1 - \theta^* - \beta^* c_1|, ..., |y_n - \theta^* - \beta^* c_n|$ 中的秩。那么，我们可以将秩分散函数写为

$$
D_n(\theta, \beta) = \sum_{i=1}^n |y_i - \theta - \beta c_i| a_i^+(R_n^+(\theta, \beta))
$$

该函数在 \((\theta, \beta)$ 上是凸的、连续的且分段线性的。因此，我们定义 $(\theta^*, \beta^*)^\top$ 的 R-estimator 为

$$
(\hat{\theta}_n^{*\text{UR}}, \hat{\beta}_n^{*\text{UR}})^\top = \underset{(\theta, \beta)^\top \in \mathbb{R}^2}{\text{argmin}} \{D_n(\theta, \beta)\}.
$$

很容易验证，在 \(D_n(\theta, \beta)$ 的连续点处，我们有

$$
\frac{\partial D_n(\theta, \beta)}{\partial \theta} = - \sum_{i=1}^n \text{sgn}(y_i - \theta - \beta c_i) a_i^+(R_n^+(\theta, \beta)) = -n^{-\frac{1}{2}} T_n(\theta, \beta)
$$

以及

$$
\frac{\partial D_n(\theta, \beta)}{\partial \beta} = - \sum_{i=1}^n c_i \text{sgn}(y_i - \theta - \beta c_i) a_i^+(R_n^+(\theta, \beta)) = -n^{-\frac{1}{2}} L_n(\theta, \beta).
$$

该结果为基于 (3.8.1) 或 (3.8.2) 分别对 \((\theta^*, \beta^*)$ 或 \((\theta, \beta)$ 进行同时 R-估计时引入加权符号秩统计量提供了动机和依据。进一步，利用渐近线性性质，我们得到对于任意（固定）\((\theta, \beta)^\top \in \mathbb{R}^2$，当 \(n \to \infty$ 时，

$$
|T_n(n^{-\frac{1}{2}}\omega_1, \omega_2) - T_n(0, 0) + \omega_1 \gamma(\phi, f)| \xrightarrow{P} 0, \quad (3.8.3)
$$

以及

$$
|L_n(\omega_1, n^{-\frac{1}{2}}\omega_2) - L_n(0, 0) + \omega_2 \gamma(\phi, f)| \xrightarrow{P} 0. \quad (3.8.4)
$$

因此，

$$
D_n(n^{-\frac{1}{2}}\omega_1, n^{-\frac{1}{2}}\omega_2) - D_n(0, 0) + \omega_1 T_n(0, 0) + \omega_2 L_n(0, 0) + \frac{\gamma(\phi, f)}{2}(\omega_1^2 + \omega_2^2) \xrightarrow{P} 0. \quad (3.8.5)
$$

上述提到的 \(D_n(\theta, \beta)$ 的凸性以及 (3.8.5) 中的逐点随机收敛，在 \((\theta, \beta)$ 且 \(\theta^2 + \beta^2 < k^2$ 上是一致的，且与 (3.8.3) 和 (3.8.4) 具有相同的一致收敛性。遵循 Jurečková 和 Sen (1996) 定理 5.5.2 的证明，我们得出当 \(n \to \infty$ 时，

$$
\left\| \begin{pmatrix} \sqrt{n}(\hat{\theta}_n^{*\text{UR}} - \theta^*) \\ (\hat{\beta}_n^{*\text{UR}} - \beta^*) \end{pmatrix} - \underset{(\theta, \beta) \in \mathbb{R}^2}{\text{argmin}} \left\{ \frac{\gamma(\phi, f)}{2} (\omega_1^2 + \omega_2^2) - \omega_1 T_n(0, 0) - \omega_2 L_n(0, 0) \right\} \right\| \xrightarrow{P} 0.
$$

因此，

$$
\begin{pmatrix} \sqrt{n}(\hat{\theta}_n^{\text{UR}}-\theta^*) \\ (\hat{\beta}_n^{\text{UR}}-\beta^*) \end{pmatrix}-\gamma^{-1}(\phi, f) \begin{pmatrix} T_n(0, 0) \\ L_n(0, 0) \end{pmatrix} \rightarrow^P 0. \quad (3.8.6)
$$

由于 R-estimator 具有变换尺度等变性质，由 (3.8.6) 可得，

$$
\begin{pmatrix} \sqrt{n}(\hat{\theta}_n^{\text{UR}}-\theta) \\ Q_n^{\frac{1}{2}}(\hat{\beta}_n^{\text{UR}}-\beta) \end{pmatrix}-\gamma^{-1}(\phi, f) \begin{pmatrix} 1 & -\sqrt{n}\bar{x}_n/Q_n^{\frac{1}{2}} \\ 0 & 1 \end{pmatrix} \begin{pmatrix} T_n(0, 0) \\ L_n(0, 0) \end{pmatrix} \rightarrow^P 0
$$

其中 \((\hat{\theta}_n^{\text{UR}}, \hat{\beta}_n^{\text{UR}})^\top$ 是指使用 \(D_n(\theta, \beta)$ 的 \((\theta, \beta)^\top$ 的 R-estimator。因此，

$$
\begin{pmatrix} \sqrt{n}(\hat{\theta}_n^{\text{UR}}-\theta) \\ \sqrt{n}(\hat{\beta}_n^{\text{UR}}-\beta) \end{pmatrix} \rightarrow^\mathcal{D} \mathcal{N}_2 \left( \begin{pmatrix} 0 \\ 0 \end{pmatrix}, \eta^2 \begin{pmatrix} 1+\frac{\bar{x}^2}{Q} & -\frac{\bar{x}}{Q} \\ -\frac{\bar{x}}{Q} & \frac{1}{Q} \end{pmatrix} \right) \text{ as } n \rightarrow \infty ,
$$

其中 \(Q = \lim_{n \rightarrow \infty} n^{-1} Q_n$ 。

### 3.8.1 斜率的受限 R-estimator

显然，如果怀疑 \(\beta$ 为 0，则 \(\beta$ 的受限 R-estimator (RRE)，记为 \(\hat{\beta}_n^{\text{RR}}$，为

$$
\hat{\beta}_n^{\text{RR}}=0 .
$$

为了克服在固定备择假设下不同大样本估计量具有相同渐近分布的困难，$\mathcal{H}_A : \beta \neq 0$，我们考虑局部备择假设

$$
K_{(n)} : \beta_{(n)}=\frac{1}{\sqrt{n}}\delta, \quad (3.8.7)
$$

其中 \(\delta$ 是一个固定数。

### 定理 3.10 在局部备择假设 \(K_{(n)}$ 下，受限 R-estimator \(\hat{\beta}_n^{\text{RR}}$ 的渐近分布偏差和 ADL$_2$-risk 分别为

$$
\text{ADB}(\hat{\beta}_n^{\text{RR}})=-\delta,
$$

$$
\text{ADL}_2\text{-risk}(\hat{\beta}_n^{\text{RR}})=\eta^2\Delta^2,\ \ \ \ \ \Delta^2=\frac{Q\delta^2}{\eta^2}.
$$

接下来，我们将定义简单线性模型 (3.8.1) 中斜率参数的收缩估计量和惩罚估计量。

### 3.8.2 斜率的收缩 R-estimator

考虑斜率的如下收缩 R-estimator

$$
\hat{\beta}_n^{\text{ShrinkageR}}(c) = c\hat{\beta}_n^{\text{UR}}, \quad 0 \le c \le 1. \tag{3.8.8}
$$

### 定理 3.11 在局部备择假设 \(K_{(n)} : \beta = n^{-\frac{1}{2}}\delta$ 下，\(\hat{\beta}_n^{\text{ShrinkageR}}(c)$ 的 ADB 和 ADL$_2$-risk 为

$$
\text{ADB}(\hat{\beta}_n^{\text{ShrinkageR}}(c)) = -(1-c)\delta = -\frac{\eta}{\sqrt{Q}}(1-c)\Delta,
$$

$$
\text{ADL}_2\text{-risk}(\hat{\beta}_n^{\text{ShrinkageR}}(c)) = \frac{\eta^2}{Q}[c^2 + (1-c)^2\Delta^2], \quad \Delta^2 = \frac{Q\delta^2}{\eta^2}. \tag{3.8.9}
$$

### 推论 3.3 斜率 \(\beta$ 的收缩 R-estimator 的最优 c 值为

$$
c_{\text{opt}} = \frac{\Delta^2}{1 + \Delta^2}.
$$

### 证明：对 (3.8.9) 关于 c 求极小，可得

$$
\frac{\partial\text{ADL}_2\text{-risk}(\hat{\beta}_n^{\text{ShrinkageR}}(c))}{\partial c} = \frac{\eta^2}{Q} [2c - 2(1-c)\Delta^2] = 0
$$

这给出了最优值 \(\Delta^2/(1 + \Delta^2)$。

将此最优值代入 (3.8.9) 得到

$$
\text{ADL}_2\text{-risk}(\hat{\beta}_n^{\text{ShrinkageR}}(c_{\text{opt}})) = \eta^2 \frac{\Delta^2}{1 + \Delta^2}.
$$

因此，

$$
\text{ADRE}(\hat{\beta}_n^{\text{ShrinkageR}}(c_{\text{opt}}) : \hat{\beta}_n^{\text{UR}}) = 1 + \frac{1}{\Delta^2}.
$$

### 3.8.3 斜率的 Ridge-type R-estimation

现在，考虑 (3.8.8)，取 \(c = 1/(1 + \lambda), \lambda > 0$。则，\(\beta$ 的 ridge-type R-estimator 为

$$
\hat{\beta}_n^{\text{ridgeR}}(\lambda) = \frac{1}{1 + \lambda} \hat{\beta}_n^{\text{UR}}.
$$

### 定理 3.12 在局部备择假设 \(K_{(n)}$ 下，\(\beta$ 的 ridge-type R-estimator，即 \(\hat{\beta}_n^{\text{ridgeR}}(\lambda)$，的 ADB 和 ADL$_2$-risk 为

