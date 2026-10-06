

## 基础：高斯贝斯规则

高斯分布的贝斯规则：

- 边缘分布：$p(x) = \mathcal{N}(x|\mu_x, \Sigma_x)$
- 条件分布：$p(y|x) = \mathcal{N}(y|Fx, \sigma_y^2I)$

### 高斯贝斯规则 1：后验概率 $p(x|y)$ 是高斯分布，其参数为：

- 均值：$\mu_{x|y} = \mu_x + \Sigma_x F^T(\sigma_y^2I + F\Sigma_x F^T)^{-1}(y - F\mu_x)$
  修正项
- 协差：$\Sigma_{x|y} = \Sigma_x - \Sigma_x F^T(\sigma_y^2I + F\Sigma_x F^T)^{-1}F\Sigma_x$
  方差/不确定性随新信息减少

与卡尔曼滤波（Kalman Filtering）中的方程相同

- 推导：利用公式 (1) 从边缘分布 $p(x)$ 和条件分布 $p(y|x)$ 构建联合分布 $p(x,y)$。利用公式 (2) 从联合分布 $p(x,y)$ 构建后验分布 $p(x|y)$。

## 基础：高斯贝斯规则

高斯分布的贝斯规则：

- 边缘分布：$p(\boldsymbol{x}) = \mathcal{N}(\boldsymbol{x}|\boldsymbol{\mu}_{\boldsymbol{x}}, \boldsymbol{\Sigma}_{\boldsymbol{x}})$
- 条件分布：$p(\mathbf{y}|\boldsymbol{x}) = \mathcal{N}(\mathbf{y}|F\boldsymbol{x}, \sigma_y^2 I)$

- 高斯贝斯规则 2：后验概率 $p(\boldsymbol{x}|\mathbf{y})$ 是高斯分布，其参数为：
  - 均值：$\mu_{\boldsymbol{x}|\mathbf{y}} = \boldsymbol{\mu}_{\boldsymbol{x}} + (\sigma_y^2 \mathbf{I} + \boldsymbol{\Sigma}_{\boldsymbol{x}}F^T F)^{-1} \boldsymbol{\Sigma}_{\boldsymbol{x}}F^T(\mathbf{y}-F\boldsymbol{\mu}_{\boldsymbol{x}})$
  - 协差：$\boldsymbol{\Sigma}_{\boldsymbol{x}|\mathbf{y}} = (\boldsymbol{\Sigma}_{\boldsymbol{x}}^{-1} + \sigma_y^{-2} F^T F)^{-1} \sigma_y^2(\sigma_y^2 \mathbf{I} + \boldsymbol{\Sigma}_{\boldsymbol{x}}F^T F)^{-1} \boldsymbol{\Sigma}_{\boldsymbol{x}}$

- 推导：使用矩阵手册（matrix cookbook）中关于贝斯规则 1 的恒等式……
  - 均值使用恒等式 $\mathbf{A}(\mathbf{I} + \mathbf{BA})^{-1} = (\mathbf{I} + \mathbf{AB})^{-1}\mathbf{A}$ (Searl恒等式)
  - 协差使用恒等式 $(\mathbf{A} + \mathbf{BC}^T)^{-1} = \mathbf{A}^{-1} - \mathbf{A}^{-1}\mathbf{C}(\mathbf{B}^{-1} + \mathbf{C}^T\mathbf{A}^{-1}\mathbf{C})^{-1}\mathbf{C}^T\mathbf{A}^{-1}$ (Woodbury恒等式)

## 基础：高斯贝斯规则

- 高斯贝斯规则 1：用于核（kernels）的推导
  - 均值：$\mu_{\boldsymbol{x}|y} = \boldsymbol{\mu}_{\boldsymbol{x}} + \boldsymbol{\Sigma}_{\boldsymbol{x}}F^T(\sigma_y^2 I + F\boldsymbol{\Sigma}_{\boldsymbol{x}}F^T)^{-1}(\boldsymbol{y} - F\boldsymbol{\mu}_{\boldsymbol{x}})$
  - 协差：$\Sigma_{\boldsymbol{x}|y} = \boldsymbol{\Sigma}_{\boldsymbol{x}} - \boldsymbol{\Sigma}_{\boldsymbol{x}}F^T(\sigma_y^2 I + F\boldsymbol{\Sigma}_{\boldsymbol{x}}F^T)^{-1}F\boldsymbol{\Sigma}_{\boldsymbol{x}}$

- 高斯贝斯规则 2：用于特征（features）的推导
  - 均值：$\mu_{\boldsymbol{x}|y} = \boldsymbol{\mu}_{\boldsymbol{x}} + (\sigma_y^2\boldsymbol{\Sigma}_{\boldsymbol{x}}^{-1} + F^T F)^{-1}F^T(\boldsymbol{y} - F\boldsymbol{\mu}_{\boldsymbol{x}})$
  - 协差：$\Sigma_{\boldsymbol{x}|y} = \sigma_y^2(\sigma_y^2\boldsymbol{\Sigma}_{\boldsymbol{x}}^{-1} + F^T F)$

不记得精确方程……记住它们的性质

- 两个规则在数学上是等价的……
- 然而，在数值上可能有巨大差异
- 贝斯规则 1：求逆一个维度为 $dim(y) \times dim(y)$ 的矩阵
- 贝斯规则 2：求逆一个维度为 $dim(x) \times dim(y)$ 的矩阵

> 如果 $dim(y) < dim(x)$，使用规则 1

## 基础：高斯传播

给定边缘分布 $p(x) = \mathcal{N}(x|\boldsymbol{\mu}_x, \boldsymbol{\Sigma}_x)$ 和条件分布 $p(y|x) = \mathcal{N}(Fx, \sigma_y^2 I)$，我们得到 $y$ 的边缘分布：

- 边缘分布 $p(y) = \int p(x)p(y|x)dx$ 是高斯分布，
  - 均值：$\boldsymbol{\mu}_y = F\boldsymbol{\mu}_x$
  - 方差：$\boldsymbol{\Sigma}_y = \sigma_y^2 I + F\boldsymbol{\Sigma}_x F^T$
  - 推导：
    利用公式 (1) 获取联合分布
    直接从联合分布读取边缘分布 $p(y)$
    $y$ 的方差由于 $x$ 的不确定性而增大

好了，准备进行贝斯回归！

## 贝斯线性回归：计算后验概率

- 似然（条件）：$p(y|\mathbf{X}, \mathbf{w}) = \mathcal{N}(\Phi\mathbf{w}, \sigma^2 I)$
- 先验（边缘）：$p(\mathbf{w}) = \mathcal{N}(\mathbf{0}, \lambda^{-1}\mathbf{I})$
- 维度：$\mathbf{w} \in \mathbb{R}^d, y \in \mathbb{R}^{N}$

由于边缘变量（参数向量）的维度小于条件变量（数据点）的维度，我们需要使用高斯规则 2！

$$\mu_{\mathbf{w}|\mathbf{X},\mathbf{y}} = \boldsymbol{\mu}_{\mathbf{w}} + (\sigma_y^2\boldsymbol{\Sigma}_{\mathbf{w}}^{-1} + F^T F)^{-1}F^T (\mathbf{y} - \boldsymbol{\mu}_{\mathbf{w}})$$
$$\boldsymbol{\Sigma}_{\mathbf{w}|\mathbf{X},\mathbf{y}} = \sigma_y^2(\sigma_y^2\boldsymbol{\Sigma}_{\mathbf{w}}^{-1} + F^T F)^{-1}$$

其中 $\boldsymbol{\mu}_{\mathbf{w}} = \mathbf{0}, \boldsymbol{\Sigma}_{\mathbf{w}} = \lambda^{-1}\mathbf{I}, \mathbf{F} = \Phi$ 且 $\sigma_{y}^2 = \sigma_y^2$

## 计算后验概率

**后验** $p(w|X, y) = \mathcal{N}(w|\mu_{w,y}, \Sigma_{w,y})$：

- 后验均值：$\mu_{w,y} = (\Phi^T\Phi + \sigma_y^2\lambda I)^{-1}\Phi^T y$
- 后验协差：$\Sigma_{w,y} = \sigma_y^2(\Phi^T\Phi + \sigma_y^2\lambda I)^{-1}$

**观察：**

- 后验均值等于 MAP 估计
- ……源于似然函数的线性性质（非线性模型不适用）
- 高斯分布的均值和众数（mode）是相同的

**那么优势是什么？**

- 我们得到了参数向量的不确定性估计！

## 示例：从后验概率采样

- 我们可以创建样本 $w_i \sim p(\boldsymbol{w}|\boldsymbol{X}, \boldsymbol{y})$
- 每个 $\boldsymbol{w}_i$ 代表一个函数 $f_i(\boldsymbol{x}) = w_i^T \phi(\boldsymbol{x})$
- 基函数由 RBF 基函数给出

![](img/f01928df5090c99ce023dd3c527a33d_849_0.png)
![](img/f01928df5090c99ce023dd3c527a33d_849_1.png)
![](img/f01928df5090c99ce023dd3c527a33d_849_2.png)
![](img/f01928df5090c99ce023dd3c527a33d_849_3.png)

## 预测分布

预测分布公式给出：

$$p(y^*|x^*,X,y) = \int p(y^*|w,x^*)p(w|X,y)dw$$

- 使用高斯传播，我们可以评估预测分布。它是高斯分布，且：
- 均值：$\mu(x^*) = \phi(x^*)^T(\Phi^T\Phi + \sigma_y^2\lambda I)^{-1}\Phi^T y$
  - 方差：$\sigma_y^2(x^*) = \sigma_y^2(1 + \phi(x^*)^T(\Phi^T\Phi + \sigma_y^2\lambda I)^{-1}\phi(x^*))$

均值部分没有新发现（与岭回归 / MAP 解决方案相同）

然而：

- 方差现在依赖于输入！
- 同时也捕获了认知不确定性（epistemic uncertainty）！

## 示例：预测分布

使用 $\mu(\boldsymbol{x}^*) \pm 2\sigma(\boldsymbol{x}^*)$ 可视化预测分布

- 如果训练数据包含特定特征的权重信息，则模型不确定性会减少
- 在 $\hat{N} \to \infty$ 的极限下，模型不确定性消失，剩下噪声方差 $\sigma_y^2$

![](img/f01928df5090c99ce023dd3c527a33d_851_0.png)

## 核心结论

* 贝斯学习包含两个步骤：
  - 计算参数/模型的后验概率
  - 根据后验概率对所有参数/模型进行加权平均
* 这两个步骤**在一般情况下是不可行的**
  - 仅对线性特征/核化回归模型有闭式解求解
  - 对于所有其他情况，我们需要**依赖近似**
* 然而，从理论上来说它是强大的学习方法之一
  - 对过拟合鲁棒（对数据点之间未指定的行为进行平均）
  - 不需要测试集
  - 能量化模型不确定性
  - **研究热点**：贝斯神经网络

