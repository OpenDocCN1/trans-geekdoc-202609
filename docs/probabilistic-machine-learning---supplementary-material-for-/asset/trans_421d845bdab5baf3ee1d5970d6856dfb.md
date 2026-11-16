

## 6.1.2.1 莫罗分解

计算某些近端算子的有用技术利用了一个被称为**莫罗分解**的结果，它指出

\(\boldsymbol{x} = \text{prox}_f(\boldsymbol{x}) + \text{prox}_{f^*}(\boldsymbol{x}) \quad (6.18)\)

其中 \(f^*\) 是 \(f\) 的凸共轭（参见第 6.5 节）。

例如，假设 \(f = || \cdot ||\) 是 \(\mathbb{R}^D\) 上的一般范数。可以证明 \(f^* = I_{\mathcal{B}}\)，其中

\(\mathcal{B} = \{ \boldsymbol{x} : ||\boldsymbol{x}||^* \le 1 \} \quad (6.19)\)

是对偶范数 \(|| \cdot ||^*\) 的单位球，定义为

\(||\boldsymbol{z}||^* = \sup \{ \boldsymbol{z}^T \boldsymbol{x} : ||\boldsymbol{x}|| \le 1 \} \quad (6.20)\)

因此

\(\text{prox}_{\lambda f}(\boldsymbol{x}) = \boldsymbol{x} - \lambda \text{prox}_{f^*/\lambda}(\boldsymbol{x}/\lambda) = \boldsymbol{x} - \lambda \text{proj}_{\mathcal{B}}(\boldsymbol{x}/\lambda) \quad (6.21)\)

因此，范数的近端算子与范数球上的投影之间存在密切联系，我们将在下文中利用这一点。

## 6.1.2.2 投影到框约束

设 \(\mathcal{C} = \{ \boldsymbol{x} : \boldsymbol{l} \le \boldsymbol{x} \le \boldsymbol{u} \}\) 为一个框或超矩形，对每个元素施加下界和上界。（如果我们不想约束某个维度上的值，这些边界可以是无限的。）投影算子很容易按元素计算，只需在边界处进行阈值处理：

\(\text{proj}_{\mathcal{C}}(\boldsymbol{x})_d = \begin{cases} l_d & \text{if } x_d \le l_d \\ x_d & \text{if } l_d \le x_d \le u_d \\ u_d & \text{if } x_d \ge u_d \end{cases} \quad (6.22)\)

例如，如果我们想确保所有元素都是非负的，可以使用

\(\text{proj}_{\mathcal{C}}(\boldsymbol{x}) = \boldsymbol{x}_+ = [\max(x_1, 0), \dots, \max(x_D, 0)] \quad (6.23)\)

## 6.1.2.3 \(\ell_1\) 范数

考虑 1-范数 \(f(\boldsymbol{x}) = ||\boldsymbol{x}||_1\)。近端投影可以按分量计算。我们可以按如下方式求解每个一维问题：

\(\text{prox}_{\lambda f}(x) = \underset{z}{\text{argmin}} \lambda |z| + \frac{1}{2}(z-x)^2 \quad (6.24)\)

可以证明，其解为

\(\text{prox}_{\lambda f}(x) = \begin{cases} x - \lambda & \text{if } x \ge \lambda \\ 0 & \text{if } |x| \le \lambda \\ x + \lambda & \text{if } x \le -\lambda \end{cases} \quad (6.25)\)

这被称为**软阈值算子**，因为绝对值小于 \(\lambda\) 的值被设为 0（阈值处理），但以可微的方式进行。这对于强制稀疏性很有用。请注意，软阈值可以更紧凑地写为

\(\text{SoftThreshold}_\lambda(x) = \text{sign}(x) (|x| - \lambda)_+ \quad (6.26)\)

其中 \(x_+ = \max(x, 0)\) 是 \(x\) 的正部分。在向量情况下，我们定义 \(\text{SoftThreshold}_\lambda(\boldsymbol{x})\) 为按元素的软阈值处理。

## 6.1.2.4 $\ell_2$ 范数

现在考虑 $\ell_2$ 范数 $f(\boldsymbol{x}) = \|\boldsymbol{x}\|_2 = \sqrt{\sum_{d=1}^D x_d^2}$。其对偶范数也是 $\ell_2$ 范数。将向量投影到相应的单位球 $\mathcal{B}$ 可以通过简单地对位于单位球外部的向量进行缩放来完成：

$\text{proj}_{\mathcal{B}}(\boldsymbol{x}) = \begin{cases} \frac{\boldsymbol{x}}{\|\boldsymbol{x}\|_2} & \|\boldsymbol{x}\|_2 > 1 \\ \boldsymbol{x} & \|\boldsymbol{x}\|_2 \le 1 \end{cases}$ (6.27)

因此，根据莫罗分解，我们有

$\text{prox}_{\lambda f}(\boldsymbol{x}) = (1 - \lambda/\|\boldsymbol{x}\|_2)_+\boldsymbol{x} = \begin{cases} (1 - \frac{\lambda}{\|\boldsymbol{x}\|_2})\boldsymbol{x} & \text{if } \|\boldsymbol{x}\|_2 \ge \lambda \\ 0 & \text{otherwise} \end{cases}$ (6.28)

如果向量的 $\ell_2$ 范数小于 \(\lambda\)，这将把整个向量设为零。因此，这被称为**块软阈值处理**。

## 6.1.2.5 平方 $\ell_2$ 范数

现在考虑使用 _平方_ $\ell_2$ 范数（缩放 0.5 倍），$f(\boldsymbol{x}) = \frac{1}{2}\|\boldsymbol{x}\|_2^2 = \frac{1}{2} \sum_{d=1}^D x_d^2$。可以证明

$\text{prox}_{\lambda f}(\boldsymbol{x}) = \frac{1}{1 + \lambda}\boldsymbol{x}$ (6.29)

这会缩小向量 $\boldsymbol{x}$ 的幅值，但不强制稀疏性。因此，这被称为**收缩算子**。

更一般地，如果 $f(\boldsymbol{x}) = \frac{1}{2}\boldsymbol{x}^\mathbf{T}\mathbf{A}\boldsymbol{x} + \boldsymbol{b}^\mathbf{T}\boldsymbol{x} + c$ 是一个二次函数，且 **A** 为正定，则

$\text{prox}_{\lambda f}(\boldsymbol{x}) = (\mathbf{I} + \lambda\mathbf{A})^{-1}(\boldsymbol{x} - \lambda\boldsymbol{b})$ (6.30)

这是一个特例，如果 \(f\) 是仿射函数，\(f(\boldsymbol{x}) = \boldsymbol{b}^\mathbf{T}\boldsymbol{x} + c\)。那么我们有 \(\text{prox}_{\lambda f}(\boldsymbol{x}) = \boldsymbol{x} - \lambda\boldsymbol{b}\)。我们在公式 (6.12) 中见过此示例。

## 6.1.2.6 核范数

一个 \(m \times n\) 矩阵 **A** 的**核范数**，也称为**迹范数**，是其奇异值的 \(\ell_1\) 范数：$f(\mathbf{A}) = \|\mathbf{A}\|_* = \|\boldsymbol{\sigma}\|_1$。将其作为正则化项可以得到低秩矩阵。其近端算子定义为

$\text{prox}_{\lambda f}(\mathbf{A}) = \sum_i (\sigma_i - \lambda)_+ \boldsymbol{u}_i \boldsymbol{v}_i^\mathbf{T}$ (6.31)

其中 $\mathbf{A} = \sum_i \sigma_i \boldsymbol{u}_i \boldsymbol{v}_i^\mathbf{T}$ 是 **A** 的奇异值分解（SVD）。此操作称为**奇异值阈值处理**。

## 6.1.2.7 投影到正定锥

考虑正半定矩阵锥 $\mathcal{C}$，并令 $f(\mathbf{A}) = I_{\mathcal{C}}(\mathbf{A})$ 为指示函数。近端算子对应于将 **A** 投影到该锥上。这可以使用以下公式计算：

$\text{proj}_{\mathcal{C}}(\mathbf{A}) = \sum_i (\lambda_i)_+ \boldsymbol{u}_i \boldsymbol{u}_i^\mathbf{T}$ (6.32)

其中 $\sum_i \lambda_i \boldsymbol{u}_i \boldsymbol{u}_i^\mathbf{T}$ 是 **A** 的特征值分解。这对于优化正半定（psd）矩阵很有用。

## 6.1.2.8 投影到概率单纯形

设 \(\mathcal{C} = \{\boldsymbol{x} : \boldsymbol{x} \ge 0, \sum_{d=1}^D x_d = 1\} = \mathbb{S}_D\) 为 \(D\) 维概率单纯形。我们可以使用以下公式投影到此集合：

\(\text{proj}_\mathcal{C}(\boldsymbol{x}) = (\boldsymbol{x} - v\mathbf{1})_+\) (6.33)

值 \(v \in \mathbb{R}$ 必须使用二分法查找。详情请参见 [PB+14, 第 183 页]。这对于优化离散概率分布很有用。

## 6.1.3 近点法（PPM）

近点法（PPM），也称为近端最小化算法，迭代应用以下更新：

\(\boldsymbol{\theta}_{t+1} = \text{prox}_{\eta_t \mathcal{L}}(\boldsymbol{\theta}_t) = \text{argmin}_\boldsymbol{\theta} \mathcal{L}(\boldsymbol{\theta}) + \frac{1}{2\eta_t}||\boldsymbol{\theta} - \boldsymbol{\theta}_t||_2^2\) (6.34)

其中我们假设 \(\mathcal{L} : \mathbb{R}^n \to \mathbb{R} \cup \{+\infty\}\) 是一个闭合正规凸函数。与直接最小化 \(\mathcal{L}$ 相比，该方法的优势在于，有时添加二次正则化可以改善问题的条件数，从而加速收敛。

## 6.1.3.1 随机和增量 PPM

PPM 可以扩展到随机设置，目标是优化 \(\mathcal{L}(\boldsymbol{\theta}) = \mathbb{E}_{q(\boldsymbol{z})} [\ell(\boldsymbol{\theta}, \boldsymbol{z})]$，通过使用以下随机更新：

\(\boldsymbol{\theta}_{t+1} = \text{prox}_{\eta_t \ell_t}(\boldsymbol{\theta}_t) = \text{argmin}_\boldsymbol{\theta} \ell_t(\boldsymbol{\theta}) + \frac{1}{2\eta_t}||\boldsymbol{\theta} - \boldsymbol{\theta}_t||_2^2\) (6.35)

其中 \(\ell_t(\boldsymbol{\theta}) = \ell(\boldsymbol{\theta}, \boldsymbol{z}_t)$ 且 \(\boldsymbol{z}_t \sim q$。得到的方法称为随机 PPM（参见例如 [PN18]）。如果 \(q$ 是与有限和目标相关的经验分布，这称为增量近点法 [Ber15]。它通常比 SGD 更稳定。

在代价函数为线性最小二乘问题的情况下，可以证明 [AEMI18] IPPM 等价于卡尔曼滤波器（??），其中后验均值等于当前参数估计 \(\boldsymbol{\theta}_t$。这种概率视角的优势在于，它还给出了后验协方差，可用于在 prox 算子内部定义一个变量度量距离函数，如公式 (6.7) 所示。我们可以使用扩展卡尔曼滤波器（??）将此扩展到非线性问题。

## 6.1.3.2 SGD 是线性化目标上的 PPM

我们现在展示 SGD 是线性化目标上的 PPM。为此，令当前迭代点处的近似为

\(\hat{\ell}_t(\boldsymbol{\theta}) = \ell_t(\boldsymbol{\theta}_t) + \boldsymbol{g}_t^\mathsf{T}(\boldsymbol{\theta} - \boldsymbol{\theta}_t)\) (6.36)

其中 \(\boldsymbol{g}_t = \nabla_\boldsymbol{\theta} \ell_t(\boldsymbol{\theta}_t)$。现在我们对这个近似目标计算近端更新：

\(\boldsymbol{\theta}_{t+1} = \text{prox}_{\eta_t \hat{\ell}_t}(\boldsymbol{\theta}_t) = \text{argmin}_\boldsymbol{\theta} \hat{\ell}_t(\boldsymbol{\theta}) + \frac{1}{2\eta_t}||\boldsymbol{\theta} - \boldsymbol{\theta}_t||_2^2\) (6.37)

我们有

\(\nabla_\boldsymbol{\theta} \left[ \ell_t(\boldsymbol{\theta}_t) + \boldsymbol{g}_t^\mathsf{T}(\boldsymbol{\theta} - \boldsymbol{\theta}_t) + \frac{1}{2\eta_t}||\boldsymbol{\theta} - \boldsymbol{\theta}_t||_2^2 \right] = \boldsymbol{g}_t + \frac{1}{\eta_t}(\boldsymbol{\theta} - \boldsymbol{\theta}_t)\) (6.38)

将梯度设为零，得到 SGD 步骤 \(\boldsymbol{\theta}_{t+1} = \boldsymbol{\theta}_t - \eta_t \boldsymbol{g}_t$。

