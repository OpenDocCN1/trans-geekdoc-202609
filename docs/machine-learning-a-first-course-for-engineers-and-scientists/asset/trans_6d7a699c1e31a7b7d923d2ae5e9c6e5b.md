

# 9 贝叶斯方法与高斯过程

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_189_0.png)

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_189_1.png)

(a) 定义在实数线上的由 $x_1$ 参数化的高斯过程，未以任何观测值为条件。蓝色的深浅与（边缘）方差（小于观测值）成正比，两个测试输入 $x_1$ 和 $x_2$ 的边缘分布用红色标出。与 9.5 节类似，我们只绘制了每个测试输出的边缘分布，但高斯过程为 $x$ 轴上的所有点定义了一个联合分布。

(b) 在点 $x_1$ 处观测到 $f(x_1)$ 后的条件高斯过程。图 (a) 中的先验分布以灰色显示。注意条件分布是如何根据观测值进行调整的。

**图 9.6：** 高斯过程。图 (a) 显示了先验分布，(b) 显示了基于一个观测值（黑点）条件后的后验分布。

## 将核回归扩展为高斯过程

获取高斯过程构造的另一种方法是将 8.2 节中的核技巧应用于 (9.11) 中的贝叶斯线性回归。线性回归、贝叶斯线性回归、核回归与高斯过程之间的关系总结在图 9.7 中。这本质上将导回到 (9.21)，其中核为协方差函数 $k(x,x')$，均值函数 $\mu(x)=0$。

现在让我们重复贝叶斯线性回归 (9.11) 的后验预测，但进行了两处变化。第一个变化是我们假设 $\theta$ 的均值和协方差为 $\boldsymbol{\mu}_0 = \mathbf{0}$ 且 $\Sigma = \mathbf{I}$。对于我们的目的来说，这个假设并非严格，但它简化了表达式。第二个变化是，在 8.1 节中线性回归模型中输入变量 $x$ 的非线性特征变换 $\boldsymbol{\Phi}(x)$。我们在符号中将 $\mathbf{X}$ 替换为 $\mathbf{\Phi}(X)$。总之：

$$p(f(x_*)|y) = N(f(x_*)|m_*, s_*^2), \quad (9.23a)$$

$$m_* = \boldsymbol{\Phi}(x_*)^T (\sigma^2 \mathbf{I} + \boldsymbol{\Phi}(X)^T \boldsymbol{\Phi}(X))^{-1} \boldsymbol{\Phi}(X)^T \mathbf{y}, \quad (9.23b)$$

$$s_* = \boldsymbol{\Phi}(x_*)^T (\mathbf{I} + \frac{1}{\sigma^2} \boldsymbol{\Phi}(X)^T \boldsymbol{\Phi}(X))^{-1} \boldsymbol{\Phi}(x_*). \quad (9.23c)$$

类似于核回归的推导，我们使用穿推矩阵等式 $\mathbf{A}(\mathbf{A}^T\mathbf{A} + \mathbf{I})^{-1} = (\mathbf{A}^T + \mathbf{I})^{-1}\mathbf{A}^T$ 来重写 $m_*$，目的是使其仅通过内积出现：

$$m_* = \boldsymbol{\Phi}(x_*)^T \boldsymbol{\Phi}(X)^T (\sigma^2 \mathbf{I} + \boldsymbol{\Phi}(X)^T \boldsymbol{\Phi}(X))^{-1} \mathbf{y}. \quad (9.24a)$$

为了以类似的方式重写 $s_*$，我们使用矩阵求逆引理 $(\mathbf{IU}-\mathbf{V})^{-1} = \mathbf{U}-\mathbf{U}(\mathbf{I}+\mathbf{VU})^{-1}\mathbf{V}$（该等式适用于维度的矩阵 $\mathbf{U}$ 和 $\mathbf{V}$），

$$s_* = \boldsymbol{\Phi}(x_*)^T \boldsymbol{\Phi}(X)^T - \boldsymbol{\Phi}(x_*)^T \boldsymbol{\Phi}(X)^T (\sigma^2 \mathbf{I} + \boldsymbol{\Phi}(X)^T \boldsymbol{\Phi}(X))^{-1} \boldsymbol{\Phi}(x_*). \quad (9.24b)$$

机器学习 - 工程师与科学家第一门课程草稿（2021年4月30日）。http://mlbook.org

190 © Andreas Lindholm, Niklas Wahlström, Fredrik Lindstein, and Thomas B. Schober 2021.

## 9.3 高斯过程

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_190_0.png)

**图 9.7：** 线性回归、贝叶斯线性回归、核岭回归与高斯过程之间关系的图形化总结。

与 (8.12) 中核岭回归的推导类似，我们现在准备应用核技巧，并将所有的 $\phi(x)\phi(x)'$ 替换为核 $k(x,x')$。使用 (8.12) 中相同的符号，我们得到：

$$m_* = K(\mathbf{x}_*, \mathbf{X})^T(\sigma^2 I + K(\mathbf{X}, \mathbf{X}))^{-1}\mathbf{y} \quad (9.25a)$$

$$\sigma_* = k(\mathbf{x}_*, \mathbf{x}_*) - K(\mathbf{x}_*, \mathbf{X})^T(\sigma^2 I + K(\mathbf{X}, \mathbf{X}))^{-1}K(\mathbf{X}, \mathbf{x}_*) \quad (9.25b)$$

后验预测由 (23a) 和 (25b) 的高斯过程模型定义，如果 $\mu(\mathbf{x}_*) = 0$ 且 $\sigma = 0$。$\mu(\mathbf{x})=0$ 的原因是推导从 $\mu_0=0$ 开始的。当我们推导 (21) 时，假设观测到了 $f(\mathbf{x})$（而不是 $y = f(\mathbf{x}) + \epsilon$）。高斯过程是贝叶斯线性回归的一个版本，岭回归是正则化线性回归的一个版本，如图7 所示。为了看到与岭回归的联系，注意 (25a) 与 (14) 在 $\sigma^2=\lambda$ 时是等价的。同样重要的是，核回归没有 (25b) 的对应项，因为核回归并不预测概率分布。

核在高斯过程中充当协方差函数的这一事实为我们提供了 8.4 节中核的另一种解释，核 $k(x,x')$ 决定了 $f(x)$ 和 $f(x')$ 之间的相关性强度。

**回顾 9.1：** 在高斯过程中使用线性核 (23) 来验证贝叶斯线性回归。为什么通常不在格姆矩阵 $K(\mathbf{X}, \mathbf{X})$ 上添加 $\sigma^2I$，而是将一个白噪声核 (22) 加到原始核 $\tilde{k}(x,x') = k(x,x') + \sigma^2\delta(x,x')$ 上？我们将 $\sigma^2 I + K(\mathbf{X}, \mathbf{X})$ 替换为 $\tilde{K}(\mathbf{X}, \mathbf{X})$，其中 $\tilde{K}$ 是使用 $\tilde{k}(x,x')$ 构建的。那么 (25) 简化为：

$$m_* = K(\mathbf{x}_*, \mathbf{X})^T\tilde{K}(\mathbf{X}, \mathbf{X})^{-1}\mathbf{y} \quad (26a)$$

$$\sigma_* = k(\mathbf{x}_*, \mathbf{x}_*) - K(\mathbf{x}_*, \mathbf{X})^T\tilde{K}(\mathbf{X}, \mathbf{X})^{-1}\tilde{K}(\mathbf{X}, \mathbf{x}_*) - \sigma^2 \quad (26b)$$

本材料将由剑桥大学出版社出版。此预览版本仅供个人免费查看和下载。禁止再发行、转售或在开发中使用。
Andreas Lindholm, Nikolai Wahlström, Fredrik Lindson, and Thomas B. Schön 2021.

# 9 贝叶斯方法与高斯过程

**数据：** 训练数据 $\mathcal{T} = \{x_i, y_i\}_{i=1}^n$，核 $\kappa(x, \mathbf{x}')$，噪声差 $\sigma^2$ 和测试输入 $\mathbf{x}_*$。
**结果：** 后验预测 $p(\mathbf{x}_*|\mathbf{y}) = N(f(\mathbf{x}_*); m_*, s_*)$

1. 根据 (25) 计算 $m_*$ 和 $s_*$

## 方法 9.2：高斯过程回归。

#### 函数上的非参数分布

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_191_0.png)

(a) 我们得到了回归过程的训练数据 $\{x_i, y_i\}_{i=1}^n$。

(b) 我们进行回归时的底层假设是存在*某个函数* $f$，描述数据 $y_i = f(x_i) + e$。它是未知的，但回归的（无论使用何种方法）是确定 $f$。

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_191_1.png)

(c) 高斯过程定义了 $f$ 的分布。我们可以以训练数据为条件（即学习），并访问任何输入，例如 $x_*$ 和 $\mathbf{x}_*$。然后我们对 $x_*$ 和 $\mathbf{x}_*$ 进行预测。高斯过程为我们提供了 $f(x_*)$ 和 $f(\mathbf{x}_*)$ 的高斯分布，用实红线表示。该分布受核选择的影响很大，而核是高斯过程中的设计选择。

**图 9.8：** 高斯过程定义了函数上的分布，我们可以以训练数据为条件，并访问任意点（如 $x_*$ 和 $\mathbf{x}_*$）来计算预测。

作为一种监督学习方法，我们使用高斯过程来做出预测，即计算后验预测 $p(f_*|\mathbf{y})$ 或 $p(y_*|\mathbf{y})$。然而，与其他大多数只提供点预测 $\tilde{y}(\mathbf{x}_*)$ 的方法不同，后验概率是一个分布。如果我们能为任何 $\mathbf{x}_*$ 计算后验预测，那么高斯过程实际上定义了一个*函数上的分布*，我们在图 9.8 中所示。

如果我们能推导出贝叶斯线性回归与 L2 正化回归之间的联系，我们也能看到高斯过程与岭回归之间存在类似的联系。如果我们只考虑后验的均值 $m_*$，我们就恢复了岭回归。为了充分利用贝叶斯视角，我们还必须考虑后验预测方差 $s_*$。对于大多数核，如果附近有数据点，预测方差会越小，

