
![](img/f01928df50903c99ce023dd3c527a33d_563_0.png)

[来自 Veliković 等人 (ICLR 2018) 的图]

```
$$\vec{h}'_i = \sigma \left( \frac{1}{K} \sum_{k=1}^K \sum_{j \in \mathcal{N}_i} \alpha_{ij}^k \mathbf{W}^k \vec{h}_j \right)$$
```

i 等人 (CVPR 2017), Vos (NIPS 2017), Veliković 等人 (ICLR 2018)

Gerhard Neumann | 机器学习 | KIT | SS 2024

## 注意力机制

### 多头注意力：

末层

$$\vec{h}_i' = \sigma \left(\frac{1}{K} \sum_{k=1}^K \sum_{j \in \mathcal{N}_i} \alpha_{ij}^k \mathbf{W}^k \vec{h}_j\right)$$

前层

$$\vec{h}_i' = \sigma \left(\sum_{j \in \mathcal{N}_i} \alpha_{ij}^k \mathbf{W}^k \vec{h}_j\right)$$

- K 个不同的头

- 在末层平均，在前层层拼接

- || 表示拼接

$$\frac{\exp\left(\text{LeakyReLU}(\vec{a} || \vec{h}_j)\right)}{\sum_{k \in \mathcal{N}_i} \exp\left(\text{LeakyReLU}(\vec{a} || \vec{h}_k)\right)}$$

### 注意力权重：$\alpha_{ij} =$

- Softmax 激活

- 由 $\mathbf{W} \in \mathbb{R}^{F' \times F}$ 和 $\vec{a} \in \mathbb{R}^{F'}$ 参数

## 带有注意力机制的图神经网络 (GNNs)

![](img/f01928df50903c99ce023dd3c527a33d_565_0.png)

优点：

- 不需要存储中间的激活值（当使用点积注意力时）

- 比带有边嵌入的 GNNs 慢

缺点：

- 表达能力可能低于带有边嵌入的 GNNs

- 可能更难优化

[来自 Veliković 等人 (ICLR 2018) 的图]

## GNNs / GCNs 的分类与链接预测

输入：特征矩阵 $X \in \mathbb{R}^{N \times E}$，预处理的邻接矩阵 $\hat{A}$

![](img/f01928df50903c99ce023dd3c527a33d_566_0.png)

节点分类：$softmax(z_n)$，例如 Kipf & Welling (ICLR 2017)

$H^{(l+1)} = \sigma \left(\hat{A}H^{(l)}W^{(l)}\right)$ $Z = H^{(L)}$

权重共享：每个消息传递层都有自己的权重

## GNNs / GCNs 的分类与链接预测

输入：特征矩阵 $X \in \mathbb{R}^{N \times E}$，预处理的邻接矩阵 $\hat{A}$

![](img/f01928df50903c99ce023dd3c527a33d_567_0.png)

$H^{(l+1)} = \sigma \left(\hat{A}H^{(l)}W^{(l)}\right)$

权重共享：每个消息传递层都有自己的权重

## GNNs / GCNs 的分类与链接预测

输入：特征矩阵 $X \in \mathbb{R}^{N \times E}$，预处理的邻接矩阵 $\hat{A}$

![](img/f01928df50903c99ce023dd3c527a33d_568_0.png)

节点分类：$softmax(\mathbf{z}_n)$，例如 Kipf & Welling (ICLR 2017)

图分类：$softmax(\sum_n \mathbf{z}_n)$，例如 Duvenaud 等人 (NIPS 2015)

链接预测：$p(A_{ij}) = \sigma(\mathbf{z}_i^T \mathbf{z}_j)$

Kipf & Welling (NIPS 2016)

“图自动编码器”

权重共享：每个消息传递层都有自己的权重

## 图上的半监督分类

设置：

某些节点已标记（黑色圆圈）

所有其他节点均未标记

任务：

预测未标记节点的标签

![](img/f01928df50903c99ce023dd3c527a33d_569_0.png)

## 图上的半监督分类

设置：

某些节点已标记（黑色圆圈）

所有其他节点均未标记

任务：

预测未标记节点的标签

![](img/f01928df50903c99ce023dd3c527a33d_570_0.png)

仅在标记节点上评估损失：

```
$$\mathcal{L} = -\sum_{l\in\mathcal{Y}_L} \sum_{f=1}^{F} Y_{lf} \ln Z_{lf}$$
```

- $\mathcal{Y}_L$ 标记节点索引集

- $\mathbf{Y}$ 标签矩阵

- $\mathbf{Z}$ GCN 输出（经过 softmax）

## 图上的半监督分类

设置：

某些节点已标记（黑色圆圈）

所有其他节点均未标记

任务：

预测未标记节点的标签

![](img/f01928df50903c99ce023dd3c527a33d_571_0.png)

仅在标记节点上评估损失：

$$\mathcal{L} = -\sum_{l \in \mathcal{Y}_L} \sum_{f=1}^{F} Y_{if} \ln Z_{if}$$

$\mathcal{Y}_L$ 标记节点索引

$Y$ 标签矩阵

$Z$ GCN 输出（经过 softmax）

| 方法 | Citeseer | Cora | Pubmed | NELL |
|---|---|---|---|---|
| ManiReg [3] | 60.1 | 59.5 | 70.7 | 21.8 |
| SemiEmb [28] | 59.6 | 59.0 | 71.1 | 26.7 |
| LP [37] | 45.3 | 58.0 | 63.0 | 26.5 |
| DeepWalk [22] | 43.2 | 67.2 | 65.3 | 25.1 |
| ICA [18] | 69.1 | 75.1 | 79.9 | 58.3 |
| Planetoid* [29] | 64.1 (6cks) | 75.7 (13s) | 77.2 (25s) | 61.0 (185s) |
| GCN (本文) | 70.3 (7s) | 81.5 (4s) | 79.0 (38s) | 66.0 (48s) |
| GCN (随机划分) | 67.9 ± 0.5 | 80.1 ± 0.5 | 78.9 ± 0.7 | 58.4 ± 1.7 |

# GNN 的突破

![](img/f01928df50903c99ce023dd3c527a33d_572_0.png)

用于确定最优路线及其旅行时间的模型架构。

致谢：Deepmind

Gerhard Neumann | 机器学习 | KIT | SS 2024

# GNN 的突破

## 全球范围内的 Google Maps ETA（预计到达时间）改进

![](img/f01928df50903c99ce023dd3c527a33d_573_0.png)

# 用于粒子模拟的 GNN

物理模拟器的巨大加速：

![](img/f01928df50903c99ce023dd3c527a33d_574_0.png)

![](img/f01928df50903c99ce023dd3c527a33d_574_1.png)

![](img/f01928df50903c99ce023dd3c527a33d_574_2.png)

![](img/f01928df50903c99ce023dd3c527a33d_574_3.png)

![](img/f01928df50903c99ce023dd3c527a33d_574_4.png)

《使用图网络学习复杂物理模拟》，Pfaff 等人，2020

Gerhard Neumann | 机器学习 | KIT | SS 2024

# 用于粒子模拟的 GNN

![](img/f01928df50903c99ce023dd3c527a33d_575_0.png)

# 用于基于网格模拟的 GNN

![](img/f01928df50903c99ce023dd3c527a33d_576_0.png)

学习到的单步模拟器

$q_i^t \rightarrow q_i^{t+1}$

更新

$p_i$

迭代展开

![](img/f01928df50903c99ce023dd3c527a33d_576_1.png)

|  |  |
|---|---|
| ○ 布料网格节点 | V |
| ○ 障碍物网格节点 |  |
| — 网格空间边 | $E^M$ |
| — 世界空间边 | $E^W$ |
| ⟶ 网格空间消息 | $e_{ij}^M$ |
| ⟶ 世界空间消息 | $e_{ij}^W$ |
| ⟶ 解码加速度 | $P_i$ |

![](img/f01928df50903c99ce023dd3c527a33d_576_2.png)

![](img/f01928df50903c99ce023dd3c527a33d_576_3.png)

![](img/f01928df50903c99ce023dd3c527a33d_576_4.png)

《使用图网络学习基于网格的模拟》，Pfaff 等人，2021

Gerhard Neumann | 机器学习 | KIT | SS 2024

# 用于基于网格模拟的 GNN

![](img/f01928df50903c99ce023dd3c527a33d_577_0.png)

并准确预测它们的动力学特性

## 结论

- 图深度学习是可行的且非常有效！

- 令人兴奋的领域：有很多新的应用和扩展（难以跟上进度）

更多应用：

- 关系推理

- 多智能体强化学习 (Multi-Agent RL)

- 用于 160 亿边图推荐的 GCN ！

![](img/f01928df50903c99ce023dd3c527a33d_578_0.png)

![](img/f01928df50903c99ce023dd3c527a33d_578_1.png)

![](img/f01928df50903c99ce023dd3c527a33d_578_2.png)

# 生成模型与散散度

机器学习，SS2023

Gerhard Neumann 教授

KIT，人类机能与机器人研究所

# 我们在讲座中到哪里了？

- 第 1 章节：机器学习基础：

* 线性回归：优化与概率视角

* 线性分类：极大似然与逻辑回归

* 最大间隔分类器：合页损失 (Hinge Loss)

* 核函数：核技巧、“无限维特征空间”

* 深度神经网络：特征提取器、反向传播、计算图

* 模型选择：偏置-方差权衡、交叉验证

- 第 2 章节：神经网络架构：

* CNNs, RNNs

* Transformers

* 图神经网络 (GNNs)

- 第 3 章节：生成模型：

* 散散度 (Divergences)

* 高斯混合模型与 EM

* 变分推断与变分贝叶

* 扩散模型

- 第 4 章节：贝叶斯学习：

* 贝叶斯学习、线性回归、高斯过程

* 深度学习

# 我们在讲座中的位置？

- 第 1 章节：机器学习基础：

* 线性回归：优化与概率视角

* 线性分类：极大似然与逻辑回归

* 最大间隔分类器：合页损失

* 核函数：核技巧、“无限维特征空间”

* 深度神经网络：特征提取器、反向传播、计算图

* 模型选择：偏置-方差权衡、交叉验证

- 第 2 章节：神经网络架构：

* CNNs & RNNs

* Transformers

* 图神经网络

- 第 3 章节：生成模型：

* 散散度

* 高斯混合模型与 EM

* 变分推断与变分贝斯

* 扩散模型

- 第 4 章节：贝叶斯学习：

* 贝叶斯学习、线性回归、高斯过程

* 深度学习

# 生成式 AI

## 生成式 AI：生成模型是近期成功的基础！

- 语言生成、图像生成、语音生成等。

![](img/f01928df50903c99ce023dd3c527a33d_582_0.png)

# 稳定扩散 (Stable Diffusion)

Stable Diffusion 是一种文本到图像的模型，能够根据任何文本生成真实的图像，让数十人在几秒钟内创作出惊叹的艺术品。

使用稳定扩散免费创作美术。

![](img/f01928df50903c99ce023dd3c527a33d_582_1.png)

| 用一句话解释机器学习很棒 | 机器学习很棒，因为它让计算机从数据中学习并预测，无需显式编程。 |
| 用一句话解释机器学习很棒 | 机器学习很棒，因为它让计算机从数据中学习并适应，在医学、交通等领域带来了突破性进展。 |

![](img/f01928df50903c99ce023dd3c527a33d_582_2.png)

在 Dreamworks 风格的大山上的大木屋

# 动机

生成模型：

- 我们想要学习一个可以从未知数据分布 $p(x)$ 或条件分布 $p(x|y)$ 采样的模型——即模型可以根据相同的输入生成不同的答案。

- 对于某些模型，我们将直接学习密度 $p(x)$ 或 $p(x|y)$

- 例如：语言模型 (transformers)、高斯混合

- 对于某些模型，我们只需要采样：

- 扩散模型、VAEs、GANs...

- （在这种情况下密度很难评估）

在讲座中，我们将学习基础知识，但更专门的课程会深入探讨这一主题

# 今天的学习目标...

# 我们今天将学习...

- 理解如何衡量分布之间的距离...

- 学习正向 KL 散度与反向 KL 散度之间的性质

- 理解为什么在生成模型中经常使用“反向 KL”

- 还有哪些散度可以使用

# 散度度量

我们可以最小化两个分布之间的散度度量

```
$q^* = \text{argmin}_q \ D(q, p^*)$
```

- 在数据分布 $p^*(x)$ 和模型 $q^*(x)$ 之间

- 散度可以视为分布之间的相似性量

存在许多散度：

| Kullback–Leibler 散度 (KL散度) | $D_{KL}(p, q) = \int \frac{p(x)}{q(x)} dx$ |
| Hellinger 距离平方 | $H^2(p, q) = 2 \int (\sqrt{p(x)} - \sqrt{q(x)})^2 dx$ |
| Jensen-Shannon 散度 | $D_{JS}(p, q) = \frac{1}{2} \int p(x) (\ln(p(x)) + \ln(q(x))) - (p(x) + q(x)) \ln(\frac{p(x) + q(x)}{2}) dx$ |
| $\alpha$-散度 | $D^{(\alpha)}(p, q) = \frac{4}{1-\alpha^2} \int (1 - p(x)/q(x))^{\frac{1+\alpha}{2}} dx$ |
| 卡方散度 | $D_{\chi2}(p, q) = \int \frac{(p(x) - q(x))^2}{p(x)} dx$ |
| $(\alpha, \beta)$ 乘积散度 | $D_{\alpha,\beta}(p, q) = \frac{2}{(1-\alpha)(1-\beta)} \int (1 - \frac{q(x)}{p(x)})^{\frac{1-\alpha}{2}} (1 - \frac{p(x)}{q(x)})^{\frac{1-\beta}{2}} p(x) dx$ |

# 最常见的散度

- **反向 KL 散度**：变分推断

KL(q(x)\|p^*(x)) = \int_{x} q(x) \log \frac{q(x)}{p^*(x)}dx

- **零强制 (Zero forcing)**：如果 $p^*(x)$ 很小，则 $q(x)$ 也必须很小

- **正向 KL 散度**：极大似然（隐式）

KL(p^*(x)\|q(x)) = \int_{x} p^*(x) \log \frac{p^*(x)}{q(x)}dx

- **概率强制 (Probability forcing)**：如果 $p^*(x)$ 很高，则 $q(x)$ 也必须很高

- **Jensen-Shannon 散度**：生成对抗网络 (GANs)

JS(p^*(x)\|q(x)) = \frac{1}{2}(KL(p^*(x)\|m(x)) + KL(q(x)\|m(x))), 其中 $m(x) = \frac{p^*(x) + q(x)}{2}

# KL 散度的性质

Kullback-Leibler 散度：

$KL(p(\mathbf{x})||q(\mathbf{x})) = \int p(\mathbf{x}) \log \frac{p(\mathbf{x})}{q(\mathbf{x})} d\mathbf{x}$$

- 始终为正：$KL(p||q) \ge 0$

- 仅仅当两个分布相等时为 0：$KL(p||q) = 0 \Leftrightarrow p = q$

- 非对称性：$KL(p||q) \neq KL(q||p)$

## 高斯分布的 KL 散度

我们也可以以闭式计算高斯密度的 KL 散度：
