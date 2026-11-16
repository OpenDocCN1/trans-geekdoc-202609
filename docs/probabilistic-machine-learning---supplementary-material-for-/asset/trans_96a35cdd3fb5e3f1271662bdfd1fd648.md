

## 第 1 章

### 简介

## 第一部分

### 基础

## 第 2 章

### 概率

### 2.1 高斯分布的更多趣味

### 2.1.1 推导 MVN 的条件分布

考虑如下形式的联合高斯分布 \(p(x_1, x_2) = \mathcal{N}(x|\mu, \Sigma)\)，其中

\(\mu = \begin{pmatrix} \mu_1 \\ \mu_2 \end{pmatrix}, \quad \Sigma = \begin{pmatrix} \Sigma_{11} & \Sigma_{12} \\ \Sigma_{21} & \Sigma_{22} \end{pmatrix}\)

在 ?? 中，我们声称

\(p(x_1|x_2) = \mathcal{N}(x_1|\mu_1 + \Sigma_{12}\Sigma_{22}^{-1}(x_2 - \mu_2), \Sigma_{11} - \Sigma_{12}\Sigma_{22}^{-1}\Sigma_{21})\)

在本节中，我们将使用 Schur 补推导此结果。

让我们将联合分布 \(p(x_1, x_2)\) 分解为 \(p(x_2)p(x_1|x_2)\)，如下所示：

\(p(x_1, x_2) \propto \exp \left\{ -\frac{1}{2} \begin{pmatrix} x_1 - \mu_1 \\ x_2 - \mu_2 \end{pmatrix}^T \begin{pmatrix} \Sigma_{11} & \Sigma_{12} \\ \Sigma_{21} & \Sigma_{22} \end{pmatrix}^{-1} \begin{pmatrix} x_1 - \mu_1 \\ x_2 - \mu_2 \end{pmatrix} \right\}\)

使用 ??，上述指数变为

\(p(x_1, x_2) \propto \exp \left\{ -\frac{1}{2} \begin{pmatrix} x_1 - \mu_1 \\ x_2 - \mu_2 \end{pmatrix}^T \begin{pmatrix} \mathbf{I} & \mathbf{0} \\ -\Sigma_{22}^{-1}\Sigma_{21} & \mathbf{I} \end{pmatrix} \begin{pmatrix} (\Sigma/\Sigma_{22})^{-1} & \mathbf{0} \\ \mathbf{0} & \Sigma_{22}^{-1} \end{pmatrix} \right.\)
\(\times \left. \begin{pmatrix} \mathbf{I} & -\Sigma_{12}\Sigma_{22}^{-1} \\ \mathbf{0} & \mathbf{I} \end{pmatrix} \begin{pmatrix} x_1 - \mu_1 \\ x_2 - \mu_2 \end{pmatrix} \right\}\)
\(= \exp \left\{ -\frac{1}{2} (x_1 - \mu_1 - \Sigma_{12}\Sigma_{22}^{-1}(x_2 - \mu_2))^T (\Sigma/\Sigma_{22})^{-1} \right.\)
\((x_1 - \mu_1 - \Sigma_{12}\Sigma_{22}^{-1}(x_2 - \mu_2)) \right\} \times \exp \left\{ -\frac{1}{2} (x_2 - \mu_2)^T \Sigma_{22}^{-1} (x_2 - \mu_2) \right\}\)

其形式如下

\(\exp(\text{quadratic form in } x_1, x_2) \times \exp(\text{quadratic form in } x_2)\)

因此，我们已成功将联合分布分解为

\(p(x_1, x_2) = p(x_1|x_2)p(x_2)\)
\(= \mathcal{N}(x_1|\mu_{1|2}, \Sigma_{1|2})\mathcal{N}(x_2|\mu_2, \Sigma_{22})\)

其中条件分布的参数可以从上述方程中直接读出，使用

\(\boldsymbol{\mu}_{1|2} = \boldsymbol{\mu}_1 + \Sigma_{12}\Sigma_{22}^{-1}(x_2 - \mu_2)\) (2.11)

\(\Sigma_{1|2} = \Sigma / \Sigma_{22} = \Sigma_{11} - \Sigma_{12}\Sigma_{22}^{-1}\Sigma_{21}\) (2.12)

我们也可以利用 \(|\mathbf{M}| = |\mathbf{M}/\mathbf{H}||\mathbf{H}|\) 这一事实来验证归一化常数是否正确：

\((2\pi)^{(d_1+d_2)/2}|\Sigma|^{\frac{1}{2}} = (2\pi)^{(d_1+d_2)/2}(|\Sigma/\Sigma_{22}||\Sigma_{22}|)^{\frac{1}{2}}\) (2.13)

\(= (2\pi)^{d_1/2}|\Sigma/\Sigma_{22}|^{\frac{1}{2}}(2\pi)^{d_2/2}|\Sigma_{22}|^{\frac{1}{2}}\) (2.14)

其中 \(d_1 = \text{dim}(x_1)\) 且 \(d_2 = \text{dim}(x_2)\)。

我们可以看到，多元正态分布的边缘化方程很简单，但条件分布方程较为复杂。我们也可以使用以下参数化将 MVN 写成 **信息形式**：

\(\Lambda \triangleq \Sigma^{-1}, \quad \eta \triangleq \Sigma^{-1}\mu\) (2.15)

此处 \(\Lambda\) 为精度矩阵，\(\eta\) 为精度加权均值。在这种形式下，可以证明边缘分布和条件分布由下式给出：

\(p(x_2) = \mathcal{N}_c(x_2|\eta_2 - \Lambda_{21}\Lambda_{11}^{-1}\eta_1, \Lambda_{22} - \Lambda_{21}\Lambda_{11}^{-1}\Lambda_{12})\) (2.16)

\(p(x_1|x_2) = \mathcal{N}_c(x_1|\eta_1 - \Lambda_{12}x_2, \Lambda_{11})\) (2.17)

为证明这一点，让我们按以下方式划分 \(\eta\)：

\(\begin{pmatrix} \eta_1 \\ \eta_2 \end{pmatrix} = \begin{pmatrix} \Lambda_{11} & \Lambda_{12} \\ \Lambda_{21} & \Lambda_{22} \end{pmatrix} \begin{pmatrix} \mu_1 \\ \mu_2 \end{pmatrix}\) (2.18)

因此

\(\eta_1 = \Lambda_{11}\mu_1 + \Lambda_{12}\mu_2\) (2.19)

\(\eta_2 = \Lambda_{21}\mu_1 + \Lambda_{22}\mu_2\) (2.20)

因此

\(\begin{pmatrix} \Lambda_{11} & \Lambda_{12} \\ \Lambda_{21} & \Lambda_{22} \end{pmatrix} = \begin{pmatrix} \Sigma_{11} & \Sigma_{12} \\ \Sigma_{21} & \Sigma_{22} \end{pmatrix}^{-1}\) (2.21)

\(= \begin{pmatrix} (\Sigma/\Sigma_{22})^{-1} & -(\Sigma/\Sigma_{22})^{-1}\Sigma_{12}\Sigma_{22}^{-1} \\ -\Sigma_{22}^{-1}\Sigma_{21}(\Sigma/\Sigma_{22})^{-1} & \Sigma_{22}^{-1} + \Sigma_{22}^{-1}\Sigma_{21}(\Sigma/\Sigma_{22})^{-1}\Sigma_{12}\Sigma_{22}^{-1} \end{pmatrix}\) (2.22)

其中左上角为

\(\Lambda_{11} = (\Sigma/\Sigma_{22})^{-1} = (\Sigma_{11} - \Sigma_{12}\Sigma_{22}^{-1}\Sigma_{21})^{-1}\) (2.23)

使用条件化的矩形式，我们有

\(\Lambda_{1|2} = \Sigma_{1|2}^{-1} = (\Sigma_{11} - \Sigma_{12}\Sigma_{22}^{-1}\Sigma_{21})^{-1} = \Lambda_{11}\) (2.24)

\(\mu_{1|2} = \mu_1 + \Sigma_{12}\Sigma_{22}^{-1}(x_2 - \mu_2)\) (2.25)

但从方程 2.22 和 2.23 中我们有

\(\Lambda_{12} = -\Lambda_{11}\Sigma_{12}\Sigma_{22}^{-1}\) (2.26)

所以

\(\mu_{1|2} = \mu_1 - \Lambda_{11}^{-1}\Lambda_{12}(x_2 - \mu_2)\) (2.27)

\(\eta_{1|2} = \Lambda_{1|2}\mu_{1|2} = \Lambda_{11}\mu_1 - \Lambda_{12}(x_2 - \mu_2)\) (2.28)

\(= \Lambda_{11}\mu_1 + \Lambda_{12}\mu_2 - \Lambda_{12}x_2 = \eta_1 - \Lambda_{12}x_2\) (2.29)

接下来我们将推导信息形式下的边缘化结果。令

\(\begin{pmatrix} \Sigma_{11} & \Sigma_{12} \\ \Sigma_{21} & \Sigma_{22} \end{pmatrix} = \begin{pmatrix} \Lambda_{11} & \Lambda_{12} \\ \Lambda_{21} & \Lambda_{22} \end{pmatrix}^{-1} \qquad (2.30)\)
\(= \begin{pmatrix} \Lambda_{11}^{-1} + \Lambda_{11}^{-1}\Lambda_{12}(\Lambda/\Lambda_{11})^{-1}\Lambda_{21}\Lambda_{11}^{-1} & -\Lambda_{11}^{-1}\Lambda_{12}(\Lambda/\Lambda_{11})^{-1} \\ -(\Lambda/\Lambda_{11})^{-1}\Lambda_{21}\Lambda_{11}^{-1} & (\Lambda/\Lambda_{11})^{-1} \end{pmatrix} \qquad (2.31)\)

因此

\(\Lambda_{22}^m = \Sigma_{22}^{-1} = \Lambda/\Lambda_{11} = \Lambda_{22} - \Lambda_{21}\Lambda_{11}^{-1}\Lambda_{12} \qquad (2.32)\)
\(\eta_2^m = \Lambda_{22}^m\mu_2^m = (\Lambda_{22} - \Lambda_{21}\Lambda_{11}^{-1}\Lambda_{12})\mu_2 \qquad (2.33)\)
\(= \Lambda_{22}\mu_2 - \Lambda_{21}\Lambda_{11}^{-1}\Lambda_{12}\mu_2 \qquad (2.34)\)
\(= (\Lambda_{21}\mu_1 + \Lambda_{22}\mu_2) - \Lambda_{21}\Lambda_{11}^{-1}(\Lambda_{11}\mu_1 + \Lambda_{12}\mu_2) \qquad (2.35)\)
\(= \eta_2 - \Lambda_{21}\Lambda_{11}^{-1}\eta_1 \qquad (2.36)\)

### 2.1.2 线性高斯系统的贝叶斯规则推导

我们现在推导高斯分布的贝叶斯规则。基本思路是推导联合分布 \(p(z, y) = p(z)p(y|z)\)，然后利用高斯条件化结果来计算 \(p(z|y)\)。

更详细地，我们按以下步骤进行。联合分布的对数如下（忽略无关常数）：

\(\log p(z, y) = -\frac{1}{2}(z - \mu_z)^T \Sigma_z^{-1}(z - \mu_z) - \frac{1}{2}(y - \mathbf{W}z - b)^T \Sigma_y^{-1}(y - \mathbf{W}z - b) \qquad (2.37)\)

这显然是一个联合高斯分布，因为它是二次型的指数。

展开涉及 \(\mathbf{z}\) 和 \(\mathbf{y}\) 的二次项，并忽略线性项和常数项，我们得到

\(Q = -\frac{1}{2}z^T \Sigma_z^{-1}z - \frac{1}{2}y^T \Sigma_y^{-1}y - \frac{1}{2}(\mathbf{W}z)^T \Sigma_y^{-1}(\mathbf{W}z) + y^T \Sigma_y^{-1}\mathbf{W}z \qquad (2.38)\)
\(= -\frac{1}{2} \begin{pmatrix} z \\ y \end{pmatrix}^T \begin{pmatrix} \Sigma_z^{-1} + \mathbf{W}^T \Sigma_y^{-1}\mathbf{W} & -\mathbf{W}^T \Sigma_y^{-1} \\ -\Sigma_y^{-1}\mathbf{W} & \Sigma_y^{-1} \end{pmatrix} \begin{pmatrix} z \\ y \end{pmatrix} \qquad (2.39)\)
\(= -\frac{1}{2} \begin{pmatrix} z \\ y \end{pmatrix}^T \Sigma^{-1} \begin{pmatrix} z \\ y \end{pmatrix} \qquad (2.40)\)

其中联合分布的精度矩阵定义为

\(\Sigma^{-1} = \begin{pmatrix} \Sigma_z^{-1} + \mathbf{W}^T \Sigma_y^{-1}\mathbf{W} & -\mathbf{W}^T \Sigma_y^{-1} \\ -\Sigma_y^{-1}\mathbf{W} & \Sigma_y^{-1} \end{pmatrix} \triangleq \Lambda = \begin{pmatrix} \Lambda_{xx} & \Lambda_{xy} \\ \Lambda_{yx} & \Lambda_{yy} \end{pmatrix} \qquad (2.41)\)

从方程 ?? 出发，并利用 \(\mu_y = \mathbf{W}\mu_z + b\) 这一事实，我们有

\(p(z|y) = \mathcal{N}(\mu_{z|y}, \Sigma_{z|y}) \qquad (2.42)\)
\(\Sigma_{z|y} = \Lambda_{xx}^{-1} = (\Sigma_z^{-1} + \mathbf{W}^T \Sigma_y^{-1}\mathbf{W})^{-1} \qquad (2.43)\)
\(\mu_{z|y} = \Sigma_{z|y}(\Lambda_{xx}\mu_z - \Lambda_{xy}(y - \mu_y)) \qquad (2.44)\)
\(= \Sigma_{z|y}(\Sigma_z^{-1}\mu_z + \mathbf{W}^T \Sigma_y^{-1}\mathbf{W}\mu_z + \mathbf{W}^T \Sigma_y^{-1}(y - \mu_y)) \qquad (2.45)\)
\(= \Sigma_{z|y}(\Sigma_z^{-1}\mu_z + \mathbf{W}^T \Sigma_y^{-1}(\mathbf{W}\mu_z + y - \mu_y)) \qquad (2.46)\)
\(= \Sigma_{z|y}(\Sigma_z^{-1}\mu_z + \mathbf{W}^T \Sigma_y^{-1}(y - b)) \qquad (2.47)\)

