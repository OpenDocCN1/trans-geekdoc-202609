

\(\hat{\boldsymbol{\beta}}_n^{\text{RLiuR}}(d) = \boldsymbol{F}_n(d)\hat{\boldsymbol{\beta}}_n^{\text{RR}},\)

其中 \(\hat{\boldsymbol{\beta}}_n^{\text{RR}}\) 是受限R估计量（RRE），由以下给出

\(\hat{\boldsymbol{\beta}}_n^{\text{RR}} = \hat{\boldsymbol{\beta}}_n^{\text{UR}} - \boldsymbol{C}_n^{-1}\boldsymbol{H}^\top \boldsymbol{G}_n^{-1}(\boldsymbol{H}\hat{\boldsymbol{\beta}}_n^{\text{UR}} - \boldsymbol{h}), \quad \boldsymbol{G}_n = \boldsymbol{H}\boldsymbol{C}_n^{-1}\boldsymbol{H}^\top.\)

那么，初步检验Liu类型R估计量（PTLRE）为

\(\hat{\boldsymbol{\beta}}_n^{\text{PTLiuR}}(d, \alpha) = \boldsymbol{F}_n(d)\hat{\boldsymbol{\beta}}_n^{\text{PTR}}(\alpha),\)

其中

\(\hat{\boldsymbol{\beta}}_n^{\text{PT}}(\alpha) = \hat{\boldsymbol{\beta}}_n^{\text{UR}} - (\hat{\boldsymbol{\beta}}_n^{\text{UR}} - \hat{\boldsymbol{\beta}}_n^{\text{RR}})I(\mathcal{L}_n \le \chi_q^2(\alpha)),\)

其中

\(\mathcal{L}_n = \frac{n(\boldsymbol{H}\hat{\boldsymbol{\beta}}_n^{\text{UR}} - \boldsymbol{h})^\top \boldsymbol{G}_n^{-1}(\boldsymbol{H}\hat{\boldsymbol{\beta}}_n^{\text{UR}} - \boldsymbol{h})}{\gamma^2}.\)

那么，Stein类型收缩Liu类型R估计量（SSLRE）的形式为

\(\hat{\boldsymbol{\beta}}_n^{\text{SSLiuR}}(d) = \boldsymbol{F}_n(d)\hat{\boldsymbol{\beta}}_n^{\text{SSR}},\)

其中

\(\hat{\boldsymbol{\beta}}_n^{\text{SSR}} = \hat{\boldsymbol{\beta}}_n^{\text{UR}} - (q - 2)(\hat{\boldsymbol{\beta}}_n^{\text{UR}} - \hat{\boldsymbol{\beta}}_n^{\text{RR}})\mathcal{L}_n^{-1}.\)

最后，正则收缩Liu类型R估计量（PRSLRE）由以下给出

\(\hat{\boldsymbol{\beta}}_n^{\text{SSLiuR}^+}(d) = \boldsymbol{F}_n(d)\hat{\boldsymbol{\beta}}_n^{\text{SSR}^+}\)

其中

\(\begin{aligned} \hat{\boldsymbol{\beta}}_n^{\text{SSR}^+} &= \hat{\boldsymbol{\beta}}_n^{\text{SSR}} - (1 - (q - 2)\mathcal{L}_n^{-1})I(\mathcal{L}_n \le q - 2)(\hat{\boldsymbol{\beta}}_n^{\text{UR}} - \hat{\boldsymbol{\beta}}_n^{\text{RR}}) \\ &= \hat{\boldsymbol{\beta}}_n^{\text{SSR}} - (\hat{\boldsymbol{\beta}}_n^{\text{UR}} - \hat{\boldsymbol{\beta}}_n^{\text{RR}})I(\mathcal{L}_n \le q - 2). \end{aligned}\)

## 8.4 渐近分布风险

对于收缩估计量的渐近分布风险，我们有以下结果。

### Theorem 8.2

在局部替代假设 $K_n : H\boldsymbol{\beta} = \boldsymbol{h} + \frac{\boldsymbol{\gamma}}{\sqrt{n}}$ 下，其中 $\boldsymbol{\gamma} = (\gamma_1, \dots, \gamma_q)^\top \neq \mathbf{0}$，

$$\left( \begin{array}{c} \sqrt{n}(\hat{\boldsymbol{\beta}}_n^{\text{ULiuR}}(d)-\boldsymbol{\beta}) \\ \sqrt{n}(\hat{\boldsymbol{\beta}}_n^{\text{RLiuR}}(d)-\boldsymbol{\beta}) \\ \sqrt{n}(\hat{\boldsymbol{\beta}}_n^{\text{ULiuR}}(d)-\hat{\boldsymbol{\beta}}_n^{\text{RLiuR}}(d)) \end{array} \right) \xrightarrow{\mathcal{D}} \mathcal{N}_{3p}\left( \begin{pmatrix} b_1 \\ b_2 \\ b_1 - b_2 \end{pmatrix}, \eta^2 V \right)$$

其中

$$b_1 = -(1-d)(C+I_p)^{-1}\boldsymbol{\beta},$$

$$b_2 = b_1 - F_d \boldsymbol{\eta}, \quad \boldsymbol{\eta} = C^{-1} H^\top G^{-1} \gamma,$$

$$V = \left( \begin{array}{ccc} F_d^\top C^{-1} F_d & F_d^\top (C^{-1} - A) F_d & F_d^\top A F_d \\ F_d^\top (C^{-1} - A) F_d & F_d^\top (C^{-1} - A) F_d & \mathbf{0} \\ F_d^\top A F_d & \mathbf{0} & F_d^\top A F_d \end{array} \right)$$

and $A = C^{-1} H^\top G^{-1} H C^{-1}$. where $G = H C^{-1} H^\top$

### Theorem 8.3

R估计量的ADL$_2$-风险由以下给出

$$\text{ADL}_2\text{-risk}(\hat{\boldsymbol{\beta}}_n^{\text{ULiuR}}(d)) = \eta^2 \text{tr}(F_d^\top C^{-1} F_d) + (1-d)^2 \beta^\top (C+I_p)^{-2} \beta,$$

$$\text{ADL}_2\text{-risk}(\hat{\boldsymbol{\beta}}_n^{\text{RLiuR}}(d)) = \eta^2 \text{tr}(F_d^\top C^{-1} F_d) - \eta^2 \text{tr}(F_d^\top A F_d) + \eta^\top F_d^\top F_d \eta + 2(1-d) \eta^\top F_d^\top (C+I_p)^{-1} \beta + (1-d)^2 \beta^\top (C+I_p)^{-2} \beta,$$

$$\text{ADL}_2\text{-risk}(\hat{\boldsymbol{\beta}}_n^{\text{PTLiuR}}(d, \alpha)) = \eta^2 \text{tr}(F_d^\top C^{-1} F_d) + \eta^\top F_d^\top F_d \eta Z(\alpha, \Delta^2) - \eta^2 \text{tr}(F_d^\top A F_d) \mathcal{H}_{q+2}(\chi_{q,\alpha}^2; \Delta^2) + 2(1-d) \eta^\top F_d^\top (C+I_p)^{-1} \beta \mathcal{H}_{q+2}(\chi_{q,\alpha}^2; \Delta^2) + (1-d)^2 \beta^\top (C+I_p)^{-2} \beta,$$

ADL$_2$-risk$(\hat{\boldsymbol{\beta}}_n^{\text{SSLiuR}}(d); \boldsymbol{\beta}) = \eta^2 \text{tr}(F_d^T C^{-1} F_d) - \eta^2(q-2) \text{tr}(F_d^T A F_d)X(\Delta^2) + (q-2)^2 \eta^T F_d^T F_d \boldsymbol{\eta} Y(\Delta^2) + 2(q-2)(1-d)\eta^T F_d^T [C + I_p]^{-1} \boldsymbol{\beta} E \left[ \chi_{q+2}^{-2}(\Delta^2) \right] + (1-d)^2 \boldsymbol{\beta}^T [C + I_p]^{-2} \boldsymbol{\beta},$

ADL$_2$-risk$(\hat{\boldsymbol{\beta}}_n^{\text{SSLiuR+}}(d)) = \text{ADL}_2\text{-risk}(\hat{\boldsymbol{\beta}}_n^{\text{SSLiuR}}(d)) - \eta^2 \left\{ \text{tr}(F_d^T A F_d) E \left[ (1-(q-2)\chi_{q+2}^{-2}(\Delta^2))^2 I(\chi_{q+2}^2(\Delta^2) \le q-2) \right] + \eta^2 \left( \boldsymbol{\eta}^T F_d^T F_d \boldsymbol{\eta} \right) E \left[ (1-(q-4)\chi_{q+4}^{-2}(\Delta^2))^2 I(\chi_{q+4}^2(\Delta^2) \le q-4) \right] \right\} - 2(\boldsymbol{\eta}^T F_d^T F_d \boldsymbol{\eta}) E \left[ ((q-2)\chi_{q+2}^{-2}(\Delta^2)-1) I(\chi_{q+2}^2(\Delta^2) \le q-2) \right] - 2(1-d)\boldsymbol{\eta}^T F_d^T [C + I_p]^{-1} \boldsymbol{\beta} E \left[ ((q-2)\chi_{q+2}^{-2}(\Delta^2)-1) I(\chi_{q+2}^2(\Delta^2) \le q-2) \right],$

其中 $\Delta^2 = \eta^2 (H \boldsymbol{\beta} - h)^T G^{-1} (H \boldsymbol{\beta} - h)$，并且

$$X(\Delta^2) = 2E \left[ \chi_{q+2}^{-2}(\Delta^2) \right] - (q-2) E \left[ \chi_{q+2}^{-4}(\Delta^2) \right]$$

$$Y(\Delta^2) = 2E \left[ \chi_{q+2}^{-2}(\Delta^2) \right] - 2E \left[ \chi_{q+4}^{-4}(\Delta^2) \right] + (q-2) E \left[ \chi_{q+4}^{-4}(\Delta^2) \right]$$

$$Z(\alpha, \Delta^2) = 2 \mathcal{H}_{q+2}(\chi_{q,\alpha}^2; \Delta^2) - \mathcal{H}_{q+4}(\chi_{q,\alpha}^2; \Delta^2).$$

## 8.5 渐近分布风险比较

在本节中，我们根据R估计量的ADL$_2$-风险函数进行比较。研究重点在于收缩Liu类型R估计量。在本节中，我们根据R估计量的ADL$_2$-风险函数进行比较。

利用C的谱分解，

$$\Gamma^T C \Gamma = \Lambda = \text{Diag}(\lambda_1, \lambda_2, ..., \lambda_p),$$

其中 $\lambda_1 \ge \lambda_2 \ge ... \ge \lambda_p > 0$，$F_d = (C + I_p)^{-1}(C + d I_p)$ 的特征值为

$$\left( \frac{\lambda_1+d}{\lambda_1+1}, \frac{\lambda_2+d}{\lambda_2+1}, ..., \frac{\lambda_p+d}{\lambda_p+1} \right)$$

而 $(C + I_p)$ 的特征值为 $(\lambda_1 + 1, \lambda_2 + 1 ... , \lambda_p + 1)$。然后，我们得到以下恒等式

$$\text{tr}(F_d^T C^{-1} F_d) = \sum_{i=1}^p \frac{(\lambda_i + d)^2}{\lambda_i(\lambda_i + 1)^2},$$

$$\beta^T (C + I_p)^{-2} \beta = \sum_{i=1}^p \frac{\theta_i^2}{(\lambda_i + 1)^2}; \quad \theta = \Gamma^T \beta,$$

$$\text{tr}(F_d^T A F_d) = \sum_{i=1}^p \frac{q_{ii}(\lambda_i + d)^2}{(\lambda_i + 1)^2},$$

其中 $q_{ii} \ge 0$ 是矩阵 $Q = \Gamma^T A \Gamma$ 的第 $i$ 个对角线元素。另外，

$$\eta^T F_d^T F_d \eta = \sum_{i=1}^p \frac{\eta_i^{*2}(\lambda_i + d)^2}{(\lambda_i + 1)^2},$$

其中 $\eta_i^*$ 是向量 $\eta^* = \eta^T \Gamma$ 的第 $i$ 个元素。同样，

$$\eta^T F_d^T (C + I_p)^{-1} \beta = \sum_{i=1}^p \frac{\theta_i \eta_i^* (\lambda_i + d)}{(\lambda_i + 1)^2}.$$

### 8.5.1 SSLRE和PTLRE的比较

我们将使用风险差异来比较不同的估计量。在这种情况下，\(\text{ADL}_2\text{-risk}(\hat{\beta}_n^{SSLiuR}(d)) - \text{ADL}_2\text{-risk}(\hat{\beta}_n^{PTLiuR}(d))\) 将非正，如果

$$\eta^T F_d^T F_d \eta \ge \frac{f_1(\Delta^2, d, \alpha)}{Z(\alpha, \Delta^2) - (q - 2)Y(\Delta^2)}, \tag{8.5.1}$$

其中

$$f_1(\Delta^2, d, \alpha) = \text{tr}(F_d^T A F_d) \{ J_{q+2}(\chi_{q,\alpha}^2; \Delta^2) - (q - 2)X(\Delta^2) \} + 2(1 - d)\eta^2 \eta^T F_d^T (C + I_p)^{-1} \beta \{ (q - 2) E(\chi_{q+2}^{-2}(\Delta^2)) - J_{q+2}(\chi_{q,\alpha}^2; \Delta^2) \}.$$

由于偏离参数 $\Delta^2 > 0$，我们假设公式 (8.5.1) 的分子和分母分别均为正或负。那么 \(\hat{\beta}_n^{SSLiuR}(d)$ 支配 \(\hat{\beta}_n^{PTLiuR}(d, \alpha)$ 当

$$\Delta^2 \le \Delta_1^2(\Delta^2, d, \alpha) = \frac{f_1(\Delta^2, d, \alpha)}{\text{Ch}_{\max}[(F_d^T F_d) C^{-1}] \{ Z(\alpha, \Delta^2) - (q - 2)Y(\Delta^2) \}},$$

