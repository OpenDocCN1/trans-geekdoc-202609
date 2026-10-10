
$KL(p^*(x)||q(x)) = \int p^*(x) \log \frac{p^*(x)}{q(x)} dx$

- **向前 (Forward forcing)**：如果 $p^*(x)$ 小，$q(x)$ 也必须小
- 容易优化
- 覆盖所有概率区域
- 需要 $p^*$ 的采样

# I 投影的优化

`arg \min_{q} KL(q(x)||p^*(x)) = \int_{x} q(x) \log \frac{q(x)}{p^*(x)} dx`

## 高斯变分近似：

- 最常用的近似

### 均场近似 (Mean-field approximation)

`q_{\mu,\sigma}(x) = \mathcal{N}(\boldsymbol{\mu}, \text{diag}(\boldsymbol{\sigma}^2))`

### 全协方差近似

`q_{\mu,\boldsymbol{\Sigma}}(x) = \mathcal{N}(\boldsymbol{\mu}, \boldsymbol{\Sigma})`

### 高斯混合模型 (GMM)近似

`q_{\theta}(x) = \sum_{o} p(o)\mathcal{N}(\boldsymbol{\mu}_{o}, \boldsymbol{\Sigma}_{o})`

## 算法：

- 贝叶斯反传播 (Bayes-By-Backprop) 重参数技巧
  - 仅适用于均场近似
  - 对于全协方差情况非常慢
- 带置信区域的自然梯度（强化学习讲座）
  - 对于全协方差情况良好
  - 已扩展到 GMM 情况 [Arenz 2020]

## 贝叶斯学习的变分推理

最小化与后验分布的 KL 散：

$KL(q(\theta)||p(\theta|\mathcal{D})) = \int_{\theta} q(\theta) \log \frac{q(\theta)}{p(\theta|\mathcal{D})} d\theta$

$= \int_{\theta} q(\theta) \log \frac{q(\theta)}{p(\mathcal{D}|\theta)p(\theta)} d\mathbf{x} + Z$

$= - \int_{\theta} q(\theta) \log p(\mathcal{D}|\theta) d\theta + KL(q(\theta)||p(\theta))$

重写为极大化问题：

$\arg\min_q KL(q(\theta)||p(\theta|\mathcal{D})) = \arg\max_q \int q(\theta) \log p(\mathcal{D}|\theta) d\theta - KL(q(\theta)||p(\theta))$

- 我们需要找到具有高似然样本的分布 `q`...
- ...并且 `q` 应该接近先验分布
- 不需要证据 `p(\mathcal{D})`！

## 回顾：VAE 的变分推理

VAE **优化的是下界**而非对数似然

$\mathcal{L}(q, p) = \int q(z) \log \left(p(\boldsymbol{x}|z) \frac{p(z)}{q(z)}\right) dz = \int q(z) \log p(\boldsymbol{x}|z)dz - KL(q(z)||p(z))$

- 为什么是下界？因为 $KL(q||p) \geq 0$，可以推导出 $\mathcal{L}(q, p) \leq \log p(\boldsymbol{x})$
- 它也被称为**证据下界 (ELBO)**，因为边缘似然通常被称为证据

使用随机梯度下降对 `p` 和 `q` 进行下界 $\mathcal{L}(q, p)$ 的**联合优化**

`q^*, p^* = \arg \max_{q,p} \mathcal{L}(q, p)`

在实践中，`q_\varphi(z), p_\varphi(\boldsymbol{x}|z)` 和 `p_\varphi(z)` 将是参数化的分布，我们对 `phi` 和 `varphi` 进行优化

## 回顾：VAE 的变分推理

**`q` 学习了什么？**

$$$$KL(q(z)||p(z|\underline{x})) = \int q(z) \log \frac{q(z)}{p(z|\underline{x})}dz = \int q(z) \log \frac{p(\underline{x})q(z)}{p(\underline{x}|z)p(z)}dz = \int q(z) \log \frac{q(z)}{p(\underline{x}|z)p(z)}dz + const$$

$= -\mathcal{L}(q,p) + const$$$$

$$\Rightarrow \arg\min_q KL(q(z)||p(z|\underline{x})) = \arg\max_q \mathcal{L}(q,p)$$

- 通过关于 `q(z)` 最大化变分下界 $\mathcal{L}(q,p)$，变分分布将近似后验分布，即 `q(z) \approx p(z|\underline{x})`
- 即为了获得 `q`，我们最小化到后验分布的 I-投影（参见第 10 节）
  - 这种最小化也称为变分推理
  - 目标随着我们的后验随解码器 `p(\underline{x}|z)` 变化

# 今日议程

变分推理：
+   - I-投影对比 M-投影
- I-投影的最小化

算法：
+   - Bayes By Backprop (基于反向传播的贝叶斯)

## Bayes - 重参数化技巧

我们希望使用以下期望目标来优化分布 `p_{\theta}(x)`

$$\theta^* = \text{argmin}_\theta \mathbb{E}_{p_{\theta}}[f(x)] = \int p_{\theta}(x)f(x)dx$$

... 并且已知 $\frac{df}{dx}(x)$。如何利用这些信息？

我们可以对期望进行重参数化：
- 引入随机变量 `\xi \sim v(\xi)`，其中 `q` 是一个简单的无参数分布（例如 `v(\xi) \sim \mathcal{N}(\mathbf{0}, \mathbf{I})`）
- 如果我们能找到一个映射 `x = h_{\theta}(\xi)` 使得 `x` 的分布符合 `x \sim p_{\theta}(x)`，那么：

$$\int p_{\theta}(x)f(x)dx = \int v(\xi)f(h_{\theta}(\xi))d\xi$$

> 我们将参数从分布 `p_{\theta}(x)` 移动到了函数 `h_{\theta}(\xi)`

## 基础：重参数化技巧

**示例：**假设 `p_{\theta}(x) = \mathcal{N}(\boldsymbol{\mu}, \boldsymbol{\Sigma})` 且 `v(\xi) = \mathcal{N}(\mathbf{0}, I)`。如果我们设置 `h_{\theta}(\xi) = \mu + \mathbf{A}^T\xi`，其中 `\theta = \{\boldsymbol{\mu}, \boldsymbol{\Sigma}\}` 且 `\mathbf{A}^T\mathbf{A} = \boldsymbol{\Sigma}`，那么 `x' = h_{\theta}(\xi)` 的分布为 `p(x') = \mathcal{N}(\boldsymbol{\mu}, \mathbf{A}^T\mathbf{A})`。

**重参数化技巧：**

$$\int p_{\theta}(x)f(x)dx = \int v(\xi)f(h_{\theta}(\xi))d\xi$$

**重参数化梯度：**

$$\nabla_{\theta}\mathbb{E}_{p_{\theta}}[f(x)] = \nabla_{\theta} \int v(\xi)f(h_{\theta}(\xi))d\xi = \int v(\xi)\frac{\partial h_{\theta}}{\partial \theta}(\xi)\frac{\partial f}{\partial x}(x)d\xi$$

- 现在可以使用梯度 $\frac{\partial f}{\partial x}$ 来计算 `\nabla_{\theta}\mathbb{E}_{p_{\theta}}[f(x)]`

## 回变分推理

**目标：** `L(\theta) = \text{KL}(q_{\theta}(x)||p^*(x)) = \int_{x} q_{\theta}(x) \left(\log q_{\theta}(x) - \log p^*(x)\right) d\mathbf{x}`

**重参数化：** 均场分布 `q_{\mu,\sigma}(x) = \mathcal{N}(\mu, \text{diag}(\sigma^2))`
- 映射定义为 `h_{\theta}(\xi) = \mu + \sigma \circ \xi`，逐元素乘积

`\nabla_{\theta} L(\theta) = \nabla_{\theta} v(\xi) \left(\log q_{\theta}(h_{\theta}(\xi)) - \log p^*(h_{\theta}(\xi))\right) d\xi`

- 关于 `\theta` 的梯度现在可以通过链式法则（反向传播）轻松获得
- 与变分推理结合时，重参数化被称为 Bayes by Backprop

# 今日议程

变分推理：
+   - I-投影对比 M-投影
- I-投影的最小化

算法：
+   - Bayes By Backprop
- GMM（高斯混合模型）近似

## 使用 GMM 的变分推理

### 高斯混合模型：

`q(x) = \sum q(o)q(x|o`，其中 `q(x|o) = \mathcal{N}(x|\mu_o, \Sigma_o)`

- 这里的 `o` 现在是隐变量
- 非常灵活，可以表示多态性
- 在强化学习（RL）中也是理想的 -> 可以学习多个解决方案！
- 可能需要许多组件

![img/f01928df50903c9ce023ddc527a33d_907_0.png]

### 问题：优化 I-投影

$$\arg \min_q \text{KL}(q(x)||p^*(x)) = \int_x q(x) \log \frac{q(x)}{p^*(x)} dx$$ 对于 GMM 是困难的（不存在解析解）

- 如何实现这一点将不会涵盖

## 结果：GMM

插图（右侧）：2D GMM 实验。目标密度也是一个 GMM
- 通过迭代添加组件来提高近似质量

示例：10 链路平面“机器人”需要到达不同的目标位置
- GMM 近似有 330 个组件

![img/f01928df50903c9ce023ddc527a33d_908_0.png](img/f01928df50903c9ce023ddc527a33d_908_0.png)

![img/f01928df50903c9ce023ddc527a33d_908_1.png](img/f01928df50903c9ce023ddc527a33d_908_1.png)

Oleg Arenz, Mingjun Zhong, Gerhard Neumann, Trust-Region Variational Inference with Gaussian Mixture Models, JMLR 2020

Gerhard Neumann | Machine Learning | KIT | SS 2024

## 更多结果：贝叶斯学习

-- 德国信贷（逻辑回归）、乳腺癌（逻辑回归）
- 扩展到高维问题（最多 200 维）具有多个模式

![img/f01928df50903c9ce023ddc527a33d_909_0.png](img/f01928df50903c9ce023ddc527a33d_909_0.png)

![img/f01928df50903c9ce023ddc527a33d_909_1.png](img/f01928df50903c9ce023ddc527a33d_909_1.png)

![img/f01928df50903c9ce023ddc527a33d_909_2.png](img/f01928df50903c9ce023ddc527a33d_909_2.png)

![img/f01928df50903c9ce023ddc527a33d_909_3.png](img/f01928df50903c9ce023ddc527a33d_909_3.png)

## 总结

我们今天学习了：
+   - 在变分推理中，我们通过优化用一个易处理的分布来近似一个不可处理的目标分布
- 变分推理被表述为逆向 KL 散最小化问题
- 逆向 KL 可以生成高质量的生成模型（无模式平均）
- 我们查看了计算逆向 KL 散梯度的不同方法
- 黑盒 VI、Bayes by Backprop、自然梯度

# 动机 – 建模不确定性

- 示例：我构建了一个犬种分类器

![](img/f01928df50903c99ce023dd3c527a33d_913_0.png)

英国牛

![](img/f01928df50903c99ce023dd3c527a33d_913_1.png)

德国牧犬

![](img/f01928df50903c99ce023dd3c527a33d_913_2.png)

我的神经网络会给出什么答案？

![](img/f01928df50903c99ce023dd3c527a33d_913_3.png)

宾犬

- 我更希望得到的答案是：我的模型对该犬种的类型不确定

# 动机 – 建模不确定性

- 图像分割中的示例

![](img/f01928df50903c99ce023dd3c527a33d_914_0.png)

我不太确定

Kendal & Gal. "计算机视觉贝叶斯深度学习需要哪些不确定性？” NIPS 2016

# 回顾：贝叶斯学习

- 1. 计算后验概率：`p(\theta|D) = \frac{p(D|\theta)p(\theta)}{p(D)}`
- 2. 积分消除后验：`p(x^*|D) = \int p(x^*|\theta)p(\theta|D) d\theta`

# 特性：

- 对于极大数据集，后验将是一个点估计 `\lim_{n\to\infty} p(\theta|\mathcal{D}_n) = \delta(\theta - \theta^*)`
  - 即贝叶斯学习将等同于极大似然
- 然而，对于较小数据集具有巨大优势！
  1. 我们知道模型在何处不确定
  2. 通过平均使得估计更稳健，过拟合更少
  3. 对于深度神经网络（DNN），由于参数量巨大，所有数据集都是小数据集

# 贝叶斯深度学习

深度神经网络

![](img/f01928df50903c99ce023dd3c527a33d_916_0.png)

极大似然

![](img/f01928df50903c99ce023dd3c527a33d_916_1.png)

全贝叶斯

![](img/f01928df50903c99ce023dd3c527a33d_916_2.png)

→

## 后验分布现在是高维的：

- 可能包含数百万个参数

![](img/f01928df50903c99ce023dd3c527a33d_916_3.png)

## 我们需要这样的方法：

- 高效的（采样将太慢）
- 可扩展的（全高斯近似不起行）

# 参数后验

- 复杂的概率分布图

![](img/f01928df50903c99ce023dd3c527a33d_917_0.png)

# 算法概述

# MAP 求解

![](img/f01928df50903c99ce023dd3c527a33d_918_0.png)

# 深度集成 (Deep Ensemble)

![](img/f01928df50903c99ce023dd3c527a33d_918_1.png)

- 对应标准的深度学习
- 训练时间的 K 倍
- 通常对于良好的后验近似是必要的

# 算法概述

## 变分推断

$$\arg \min_q KL(q(x)||p^*(x)) = \int q(x) \log \frac{q(x)}{p^*(x)} dx$$

- 反向贝叶斯（较慢）
- 自然梯度
- 大多数情况下使用对角高斯分布，但使用低秩近似

![](img/f01928df50903c99ce023dd3c527a33d_919_0.png)

# 算法概述

# 蒙特卡洛 Dropout (Monte-Carlo Dropout)

# SWAG

![](img/f01928df50903c99ce023dd3c527a33d_920_0.png)

![](img/f01928df50903c99ce023dd3c527a33d_920_1.png)

- 参数上具有独立的伯努利分布
- 需要比 MAP 更多的训练
- 从 SGD 轨迹构建低秩高斯分布
- 在来自 SGD 的样本上形成

# 算法概述

# Multi-X

![](img/f01928df50903c99ce023dd3c527a33d_921_0.png)

# 采样

![](img/f01928df50903c99ce023dd3c527a33d_921_1.png)

- 集成任何单模态算法
- 使用马尔可夫链从真实后验中采样
- 昂昂的

# 特定算法

存在许多不同的算法……我们将仔细观察其中两种：
- 蒙特卡洛 Dropout
- SWAG

两者都可以应用于 Multi-X 设置中

# 蒙特卡洛 Dropout

蒙特卡洛 Dropout 可以被建模为贝叶斯框架——在一个模型中的多个模型（集成）：
- 线性层：`x_2 = Wx_1`
- 带有 dropout：`x_2 = W(x_1 \circ m)`
