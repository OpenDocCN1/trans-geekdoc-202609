

情况 1：假设 \(\eta^T F_d^T(C + I_p)^{-1} \beta\) 为正，则 Eq. (8.5.4) 的右侧为负，因为 \(\eta^T F_d^T(C + I_p)^{-1} \beta\) 是正随机变量的期望，故为正。因此，对所有 \(\Delta^2\) 和 \(d\)

\[ ADL_2-risk(\hat{\beta}_n^{SSLiur+}(d)) \le ADL_2-risk(\hat{\beta}_n^{SSLiur}(d)). \]

因此，在此条件下，PRLRE 不仅证实了 SSLRE 的不可采性，还为病态条件数据提供了一个简单的优越估计量。

情况 2：假设 \(\eta^T F_d^T(C + I_p)^{-1} \beta\) 为负，则当

\[ \eta^T F_d^T F_d \eta \ge \frac{f_5(\Delta^2, d)}{g_4(\Delta^2)}, \tag{8.5.5} \]

时，Eq. (8.5.4) 的差值将为正，其中

\[ f_5(\Delta^2, d) = 2(1 - d)\eta^T F_d^T(C + I_p)^{-1} \beta \, a_3 - \eta^2 tr(F_d^T A F_d) \, a_1 \]

和

\[ g_4(\Delta^2) = -(a_2 + 2a_3) \].

由于 \(\Delta^2 > 0\)，假设 Eq. (8.5.6) 的分子和分母分别均为正或负。则当

\[ \Delta^2 \le \Delta_5^2(\Delta^2, d) = \frac{f_6(\Delta^2, d)}{Ch_{\max}[(F_d^T F_d)C^{-1}] \times g_7(\Delta^2)} \]

时，\(\hat{\beta}_n^{SSLiur+}(d)\) 支配 \(\hat{\beta}_n^{SSLiur}(d)\)，而当

\[ \Delta^2 > \Delta_6^2(\Delta^2, d) = \frac{f_9(\Delta^2, d)}{Ch_{\min}[(F_d^T F_d)C^{-1}] \times g_7(\Delta^2)}. \]

时，\(\hat{\beta}_n^{SSLiur}(d)\) 支配 \(\hat{\beta}_n^{SSLiur+}(d)\)。

## 8.5.4 刘型秩次估计量与其对应量的比较

此处，我们仅考虑原假设不成立的情况，因为这更具一般性。此外，我们仅将 SSLRE 与 SSRE 进行比较。有关更多细节及类似比较，我们请读者参阅 Arashi et al. (2014)。

SSRE 与 SSLRE 之间的风险差为

\[
\begin{aligned}
ADL_2-risk(\hat{\beta}_n^{SSR}) - ADL_2-risk(\hat{\beta}_n^{SSLiur}(d)) = \\
\eta^2 tr(C^{-1} - F_d^T C^{-1} F_d) - \eta^2(q - 2)tr(A - F_d^T A F_d)X(\Delta^2) \\
+(q - 2)\eta^T(I - F_d^T F_d)\eta Y(\Delta^2) \\
+2(q - 2)(1 - d)\eta^T F_d^T[C + I_p]^{-1} \beta \mathbb{E} \left[ \chi_{q+2}^{-2}(\Delta^2) \right] \\
+(1 - d)^2 \beta^T [C + I_p]^{-2} \beta.
\end{aligned}
\]

当

\[ \eta^T(I - F_d^T F_d)\eta \ge \frac{h_1(\Delta^2, d)}{Y(\Delta^2)} \]

时，上述差值将大于或等于 0，其中

\[
\begin{aligned}
h_1(\Delta^2, d) = -\eta^2 \text{tr}(C^{-1} - F_d^T C^{-1} F_d) &+ \eta^2(q - 2) \text{tr}(A - F_d^T A F_d)X(\Delta^2) \\
&- 2(q - 2)(1 - d)\eta^T F_d^T [C + I_p]^{-1} \beta E \left[ \chi_{q+2}^{-2}(\Delta^2) \right] \\
&-(1 - d)^2 \beta^T [C + I_p]^{-2} \beta.
\end{aligned}
\]

由于 \(\Delta^2 > 0\)，我们假设 Eq. (8.5.6) 的分子为正。那么，每当 \(\Delta^2 \le \Delta_2^2(\Delta^2, d)\) 时，SSLRE 将支配 SSRE，其中

\[ \Delta_2^2(\Delta^2, d) = \frac{h_1(\Delta^2, d)}{(q - 2)Ch_{\max}[(I - F_d^T F_d)C^{-1}]Y(\Delta^2)}. \]

然而，当

\[ \Delta^2 < \Delta_g^2(\Delta^2, d) = \frac{h_1(\Delta^2, d)}{(q - 2)Ch_{\min}[(I - F_d^T F_d)C^{-1}]Y(\Delta^2)}. \]

时，SSRE 支配 SSLRE。

然后，我们基于偏置参数 \(d\) 比较这两个估计量。就我们的目的而言，有

\[
\begin{aligned}
ADL_2-risk(\hat{\beta}_n^{SSLiUR}(d)) = \eta^2 \sum_{i=1}^p \frac{(\lambda_i + d)^2}{\lambda_i(\lambda_i + 1)^2}
- \eta^2 \sum_{i=1}^p \frac{(q - 2)q_i(\lambda_i + d)^2}{(\lambda_i + 1)^2}X(\Delta^2) \\
+ 2(q - 2)(1 - d) \sum_{i=1}^p \frac{\theta_i \eta_i^*(\lambda_i + d)}{(\lambda_i + 1)^2} E \left[ \chi_{q+2}^{-2}(\Delta^2) \right] \\
+ \sum_{i=1}^p \frac{(q - 2)\eta_i^{*2}(\lambda_i + d)^2}{(\lambda_i + 1)^2}Y(\Delta^2)
+ (1 - d)^2 \sum_{i=1}^p \frac{\theta_i^2}{(\lambda_i + 1)^2}.
\end{aligned}
\]

现在，对偏置参数 \(d\) 求 Eq. (8.5.7) 的导数，我们得到

\[
\begin{aligned}
\frac{\partial ADL_2-risk(\hat{\beta}_n^{SSLiUR}(d))}{\partial d} = \eta^2 \sum_{i=1}^p \frac{2(q - 2)}{\lambda_i(\lambda_i + 1)^2} \\
\times \{(\lambda_i + d) - \lambda_i q_{ii}(\lambda_i + d)X(\Delta^2) + \eta^2 \lambda_i \eta_i^{\star 2} (\lambda_i + d)Y(\Delta^2) \\
+ \eta^2 \lambda_i (\theta_i \eta_i^\star - \theta_i \eta_i^\star \lambda_i - 2\theta_i \eta_i^\star d) \mathbb{E} [ \chi_{q+2}^{-2}(\Delta^2) ] - (q-2)^{-1} \eta^2 \lambda_i (1-d) \theta_i^2 \} \\
= \eta^2 \sum_{i=1}^p \frac{2}{(\lambda_i + 1)^2} (h_2(\Delta^2, \alpha)d - h_3(\Delta^2, \alpha))
\end{aligned}
\]

其中

\[ h_2(\Delta^2, \alpha) = \min_i \{ 1 - \lambda_i q_{ii} X(\Delta^2) + \eta^{-2} \lambda_i \eta_i^{\star 2} Y(\Delta^2) - 2\eta^{-2} \lambda_i \theta_i \eta_i^\star \mathbb{E} [ \chi_{q+2}^{-2}(\Delta^2) ] + (q-2)^{-1} \eta^{-2} \lambda_i \theta_i^2 \} \]

和

\[ h_3(\Delta^2, \alpha) = \max_i \{ \lambda_i ( \lambda_i q_{ii} X(\Delta^2) - 1 - \eta^{-2} \lambda_i \eta_i^{\star 2} Y(\Delta^2) - \tau_\psi^{-2} \theta_i \eta_i^\star (1 - \lambda_i) + (q-2)^{-1} \eta^2 \theta_i^2 ) \} \]

现在定义

\[ d_3(\Delta^2, \alpha) = \frac{h_2(\Delta^2, \alpha)}{h_3(\Delta^2, \alpha)} \]

假设 \(d > 0\)，则有：

- 1. 如果 \(h_i(\Delta^2, \alpha) > 0, i = 2, 3\)，则对于每个满足 \(d > d_3(\Delta^2, \alpha)\) 的正 \(d\)，\(\hat{\beta}_n^{SSLiUR}(d)\) 的风险值小于 \(\hat{\beta}_n^{SSR}\) 的风险值。
- 2. 如果 \(h_i(\Delta^2, \alpha) < 0, i = 2, 3\)，则对于每个满足 \(d < d_3(\Delta^2, \alpha)\) 的正 \(d\)，\(\hat{\beta}_n^{SSLiUR}(d)\) 的风险值小于 \(\hat{\beta}_n^{SSR}\) 的风险值。

## 8.6 \(d\) 的估计

考虑 ULRE 的 ADL_2 风险由

\[
\begin{aligned}
f(d) = ADL_2-risk(\hat{\beta}_n^{ULiUR}(d)) &= \eta^2 tr(F_d^\top C^{-1} F_d) + (1-d)^2 \beta^\top (C + I_p)^{-2} \beta, \\
&= \eta^2 \sum_{i=1}^p \frac{(\lambda_i + d)^2}{\lambda_i (\lambda_i + 1)^2} + (1-d)^2 \sum_{i=1}^p \frac{\theta_i^2}{(\lambda_i + 1)^2} \\
&= \delta_1(d) + \delta_2(d). \tag{8.6.1}
\end{aligned}
\]

对于刘估计量，人们希望找到一个 \(d\) 值，使得方差的减少（\(\delta_1(d)\)）大于平方偏差的增加（\(\delta_2(d)\)）。为了证明存在一个小于 1 的 \(d\) 值，使得

\[ \text{ADL}_2\text{-risk}(\hat{\beta}_n^{\text{ULiuR}}(d)) < \text{ADL}_2\text{-risk}(\hat{\beta}_n^{\text{UR}}), \]

我们将对 Eq. (8.6.1) 关于 \(d\) 求导，如下所示，

\[ \frac{\partial f(d)}{\partial d} = 2\eta^2 \sum_{i=1}^p \frac{(\lambda_i + d)}{\lambda_i(\lambda_i + 1)^2} - 2(1 - d) \sum_{i=1}^p \frac{\theta_i^2}{(\lambda_i + 1)^2}. \tag{8.6.2} \]

在 Eq. (8.6.2) 中取 \(d = 1\)，得到

\[ \frac{\partial f(d)}{\partial d} = 2 \sum_{i=1}^p \frac{1}{\lambda_i(\lambda_i + 1)} > 0, \quad \text{since } \lambda_i \ge 0. \tag{8.6.3} \]

因此，存在一个 \(d\) 值（\(0 < d < 1\)），使得

\[ \text{ADL}_2\text{-risk}(\hat{\beta}_n^{\text{ULiuR}}(d)) < \text{ADL}_2\text{-risk}(\hat{\beta}_n^{\text{UR}}). \]

现在由 Eq. (8.6.2)，\(\hat{\beta}_n^{\text{ULiuR}}(d)\) 的风险在

\[ d = \frac{\sum_{i=1}^p \frac{\theta_i^2 - \tau^2}{(\lambda_i + 1)^2}}{\sum_{i=1}^p \frac{(\eta^2 + \lambda_i \theta_i^2)}{\lambda_i(\lambda_i + 1)^2}}, \]

处最小化，其中 \(\theta_i\) 是向量 \(\theta = \Gamma^\text{T} \beta\) 的第 \(i\) 个分量。将 \(\theta_i^2\) 和 \(\eta^2\) 替换为它们各自的无偏估计 \(\left(\hat{\theta}_i^{\text{UR}}\right)^2 - \frac{\hat{\sigma}^2}{\lambda_i}\) 和 \(\hat{\eta}^2\)，我们得到 \(d\) 的最优值为

\[ d_{\text{opt}} = 1 - \eta^2 \left\{ \frac{\sum_{i=1}^p \frac{1}{\lambda_i(\lambda_i+1)}}{\sum_{i=1}^p \frac{(\hat{\theta}_i^{\text{UR}})^2}{(\lambda_i+1)^2}} \right\}. \]

关于 \(d\) 估计的更多信息，请参阅 Akdeniz and Ozturk (2005) 和 Arashi et al. (2017b) 等文献。

## 8.7 糖尿病数据分析

在本节中，我们通过采用 Arashi et al. (2018) 的一个真实示例，对刘估计量进行性能分析。该数据集包含 10 个协变量：年龄、性别、身体质量指数 (BMI)、血压 (BP) 和六项血液

![](img/f3b106d7e76ae3afcec8895afa28732c_313_0.png)

| 变量 | Age | Sex | BMI | BP | S1 | S2 | S3 | S4 | S5 | S6 |
|---|---|---|---|---|---|---|---|---|---|---|
| VIF | 1.22 | 1.28 | 1.51 | 1.46 | 59.20 | 39.19 | 15.40 | 8.89 | 10.07 | 1.48 |

血清测量值，S1、S2、S3、S4、S5 和 S6，针对每个 \(n = 442\) 名患者。响应变量是随访 1 年后疾病进展的定量指标。本研究的目的是检查与重要预后变量相关的疾病进展。请注意，在开始分析之前，预测变量已标准化为均值为零、方差为一。

首先，我们验证了该数据集的特征：Bonferroni 检验报告第 57 个观测值为离群值；图 8.1 的左图证实了这一点。残差分布在图 8.1 的右侧图示，表明其服从正态模型。为了验证多重共线性，表 8.1 报告了 VIF 值。这些值表明变量 S1-S5 存在多重共线性。因此，该数据集非常适合我们的拟议用途。

### 8.7.1 惩罚估计量

为了比较和适应书籍的其他部分，我们根据 Eq. (8.2.1) 的模型设置再次给出惩罚估计量。惩罚回归方法的关键思想是最小化形式为

\[ J_{\rho, \lambda}(\boldsymbol{\beta}) = (\mathbf{y} - \mathbf{X}\boldsymbol{\beta})^{\top}(\mathbf{y} - \mathbf{X}\boldsymbol{\beta}) + \lambda P_{\rho}(\boldsymbol{\beta}) \tag{8.7.1} \]

的目标函数 \(J_{\rho, \lambda}(\boldsymbol{\beta})\)，以获得参数的估计值。目标函数的第一项是平方误差损失之和，Eq. (8.7.1) 的第二项是惩罚函数，\(\lambda\) 是一个调节参数，用于控制 \(J_{\rho, \lambda}(\boldsymbol{\beta})\) 两个组成部分之间的权衡。

