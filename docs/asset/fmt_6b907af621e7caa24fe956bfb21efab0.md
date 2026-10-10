
$m \sim \text{Bernoulli}(p), \quad p = \text{Dropout 概率}$

![](img/f01928df50903c99ce023dd3c527a33d_923_0.png)

# 二值 Dropout (Binary Dropout)

多个掩码……$y = Wx$ $x_{2,j} = \sum_{i} w_{ij}x_{1,i}m_i \leftrightarrow y = W \odot m$

# 权重分布建模

权重分布可以通过狄拉克分布建模

![](img/f01928df50903c99ce023dd3c527a33d_925_0.png)

$$q(W|\mu) = \prod_i q(w_i|\mu_i) \text{ 在 0 和 }\mu \text{ 处的狄拉克脉冲}$$

$$q(w_i|\mu) = p \delta(0) + (1 - p) \delta(\mu_i)$$

# 贝叶斯学习的变分推断

## 重构为最大化问题：

$$\text{argmin}_q KL(q(\theta)||p(\theta|D)) = \text{argmax}_q \int_{\theta} q(\theta) \log p(\mathcal{D}|\theta) d\theta - KL(\theta)||p(\theta))$$

- 我们需要找到具有高似然样本的分布 $q$……
- ……且 $q$ 应该接近先验

# 作为变分推断的 MCD

贝叶斯学习的变分推断

先验：$p(W) = \prod_{i,j} p(w_{ij}), \ p(w_{ij}) = \mathcal{N}(0, 1)$

近似后验：$q(W|\mu) = \prod_{i} q(w_i|\mu_i)$ $p$ 是一个固定的超参数！

$q(w_i|\mu_i) = p \delta(0) + (1 - p) \delta(\mu_i)$

# 双重下降 (Double Descent)

![](img/f01928df50903c99ce023dd3c527a33d_936_0.png)

## 贝斯模型是否会经历双重下降？

# 贝斯模型平均缓解双重下降

![](img/f01928df50903c99ce023dd3c527a33d_937_0.png)

贝斯深度学习与泛化的概率视角。Wilson & Izmailov, 2020

# WILDS：一个具有分布偏移的数据集

| | 领域泛化 | | | 子群体偏移 | | 领域泛化 + 子群体偏移 | | |
|---|---|---|---|---|---|---|---|------|
| 数据集 | WildCam | Camelyon17 | FxPx1 | OGB-MolPCBA | GlobalWheat | CivilComments | FMoW | PovertyMap | Amazon | Py150 |
| 输入 (x) | 相机 | 陷阱照片 | 组织切片 | 细胞图像 | 分子图 | 小麦图像 | 在线卫星图像 | 产品评论 | 代码 | | |
| 预测 (y) | 动物物种 | 肿瘤 | 扰动基因 | 生物测 | 小麦穗 | 边界框 (bbox) | 毒性 | 土地利用 | 资产财富 | 情感 | 自动完成 |
| 领域 (d) | 相机 | 医院 | 批次 | 骨架 | 位置 | 时间、人口统计 | 区域、国家、城乡 | 用户 | git 仓库 | | |
| # 需求 | 323 | 5 | 51 | 120,084 | 47 | 16 | 16 x 5 | 23 x 2 | 2,586 | 8,421 |
| # 示例 | 203,029 | 455,954 | 125,510 | 437,929 | 6,515 | 448,000 | 523,846 | 19,669 | 539,502 | 150,000 |

训练示例

![](img/f01928df50903c99ce023dd3c527a33d_938_0.png)

![](img/f01928df50903c99ce023dd3c527a33d_938_1.png)

![](img/f01928df50903c99ce023dd3c527a33d_938_2.png)

> 黑人和 LGGT 社区的人与自行车许可证有什么关系？

![](img/f01928df50903c99ce023dd3c527a33d_938_3.png)

> 总体来说，这是一个质量良好的包装包，物有所值。

```python
import numpy as np
```

测试示例

![](img/f01928df50903c99ce023dd3c527a33d_938_4.png)

![](img/f01928df50903c99ce023dd3c527a33d_938_5.png)

![](img/f01928df50903c99ce023dd3c527a33d_938_6.png)

> 作为一名基督徒，我不会资助任何这些信仰。

![](img/f01928df50903c99ce023dd3c527a33d_938_7.png)

> “我喜欢我的法语，它太完美了，而且包含了这一切！”

```python
import subprocess
as sp
p=sp.Popen(out=
```

改编自

Beery et al. 2020

Bandi et al. 2018

Taylor et al. 2019

Hu et al. 2020

David et al. 2021

Borkan et al. 2019

Christie et al. 2020

Yeh et al. 2019

Raychev et al.

# 分布偏移

- 主要问题是分布偏移
- 即我们要求网络处理它未见过的数据（分布外数据）
- 神经网络经常产生错误的答案
- 然而……它们对此非常有信心

典型行为：深度神经网络是过度自信的

- 示例：CIFAR 100
- 从图像中预测 100 个不同的类别
- 预测结果通常还带有一个置信度 ![](img/f01928df50903c99ce023dd3c527a33d_939_0.png)

# 深度学习中的过度自信

让我们在测试期间应用不同的噪声水平（即分布外数据）

![](img/f01928df50903c99ce023dd3c527a33d_940_0.png)

**置信度 (Confidence):** 神经网络（平均而言）有多自信

**准确率 (Accuracy):** 实际的预测误差是多少？

**观察结果：**

- 置信度和准确率之间总是存在差距（这种差距被称为校准）
- 分布偏移越大，这个差距通常会变得越大

# 深度学习的校准

如果具有特定置信度概率的预测以相同的概率准确，则该网络是良好校准的，即：

$p(\hat{y} = y|conf(x)) = p, \forall p \in [0,1]$

置信度图：

![](img/f01928df50903c99ce023dd3c527a33d_941_0.png)

$ECE = \mathbb{E}_{p\sim\mathcal{U}([0,1]),x\in\mathcal{D}} [|p(\hat{y} = y|conf(x) = p) - p|]$

# 在 WILDS 上的结果

![](img/f01928df50903c99ce023dd3c527a33d_942_0.png)

![](img/f01928df50903c99ce023dd3c527a33d_942_1.png)

![](img/f01928df50903c99ce023dd3c527a33d_942_2.png)

(a) iWILDCAM-WILDS

(b) FMoW-WILDS

(c) RXRx1-WILDS

- 集成方法通常具有更好的校准和更高的准确率
- MultiSWAG 和 MultiMCD 表现最佳

F. Seligann, ... , G. Neumann, Beyond Deep Ensembles: A Large-Scale Evaluation of Bayesian Deep Learning under Distribution Shift, NeurIPS 2023

# 在预训练 Transformer 上的结果

- 集成方法的优势不那么明显
- 变分推理 (BBB = Bayes by Backprob) 似乎是赢者

![](img/f01928df50903c99ce023dd3c527a33d_943_0.png)

![](img/f01928df50903c99ce023dd3c527a33d_943_1.png)

(a) CIVILCOMMENTS-WILDS

(b) AMAZON-WILDS

# 总结

我们今天学了什么：

- 标准神经网络是过度自信的
- 贝斯深度学习可以显著改进
- 集成方法通常具有更好的校准和更高的准确率
- 主要问题是分布偏移
- 贝斯模型平均缓解双重下降
- 变分推理 (BBB = Bayes by Backprob) 似乎是赢者
- MultiSWAG 和 MultiMCD 表现最佳

# 黑盒超参数优化

## 方法：

- 网格搜索
- 随机搜索
- 贝叶斯优化

![](img/f01928df50903c99ce023dd3c527a33d_952_0.png)

- 黑盒函数的评估代价高昂 $\Rightarrow$ 样本效率至关重要

## 网格搜索与随机搜索

- 两者完全没有先验信息
- 随机搜索能更好地处理不重要的维度
- 随机搜索是一个非常有用的基准

![](img/f01928df50903c99ce023dd3c527a33d_953_0.png)

图片来源：Bergstra & Bengio, JMLR 2012

## 贝叶斯优化

## 今日的学习目标...

在本节课程中，我们将..

- 介绍贝叶斯优化 (BO) 作为一种主动学习框架 ...
- ... 它是一种数据高效的黑盒优化框架
- BO 使用更具针对性的探索来进行样本生成

## 为什么选择贝叶斯优化？

- 我们所知最高效的黑盒优化器
- 对探索的原则化处理
- 广泛应用于自动机器学习 (AutoML)：自动超参数调优
- 扩展性有限（10-20 个参数）
- 计算开销非常大

![](img/f01928df50903c99ce023dd3c527a33d_955_0.png)

## 贝叶斯优化 (BO)

- 在输入空间的不同位置按顺序收集观测值
- 利用输入空间的底层结构 $\Rightarrow$ 核函数回归
- 贝叶斯视角：建模期望和不确定性 $\Rightarrow$ 高斯过程
- 预算用尽后，推荐最佳位置

![](img/f01928df50903c99ce023dd3c527a33d_956_0.png)

## 回顾：高斯过程

- 函数空间上的分布
- 即使在无限特征空间下，也能对函数进行可处理的贝叶斯建模
- 输入空间（搜索空间） $\mathcal{X}$
- 核函数 $k: \mathcal{X} \times \mathcal{X} \to \mathbb{R}$

任何有限的 N 个点集合 $\{x_1, \dots, x_N\}$ 都会导出一个 N 维高斯分布，该分布是 $\{f(x_1), \dots, f(x_N)\}$ 的后验分布

![](img/f01928df50903c99ce023dd3c527a33d_957_0.png)

## 高斯过程

高斯过程 (GP) $f(\boldsymbol{x}) \sim \mathcal{GP}(m(\boldsymbol{x}), k(\boldsymbol{x}, \boldsymbol{x}'))$ 均值函数和协方差函数关于函数 $f(\boldsymbol{x})$ 的概率分布，使得在输入 $\boldsymbol{x}_1, \dots, \boldsymbol{x}_n$ 评估的任何有限函数值 $t_i = f(\boldsymbol{x}_i)$ 都服从联合高斯分布

-- 均值函数评估了我们对函数的先验信念

  $\mathbb{E}[f(\boldsymbol{x})] = m(\boldsymbol{x})$

  - 为了简单起见，我们将 $m(\boldsymbol{x}) = 0$

- 协方差函数评估了在输入 $\boldsymbol{x}, \boldsymbol{x}'$ 处的两个函数评估值之间的相似性/相关性

  $\mathbb{E}[f(\boldsymbol{x})f(\boldsymbol{x}')] = k(\boldsymbol{x}, \boldsymbol{x}')$

  - 协方差函数需要是一个正定函数（类似于核函数）

## 示例：高斯核

高斯核定义为：

```
$k(\boldsymbol{x}, \boldsymbol{y}) = \exp\left(-\frac{\|\boldsymbol{x} - \boldsymbol{y}\|^2}{2\sigma^2}\right)$
```

其中 $\sigma$ 是带宽

![](img/f01928df50903c99ce023dd3c527a33d_959_0.png)

通常也称为：

- 径基函数核 (RBF)
- 平方指数核

它是核方法中**最常用的核**

## 高斯过程先验

$\mathcal{GP}$ : 从 $\mathcal{X}$ 到 $\mathbb{R}$ 的函数分布

先验 $\mathcal{GP}$

![](img/f01928df50903c99ce023dd3c527a33d_960_0.png)

## 高斯过程后验

$\mathcal{GP}$ : 从 $\mathcal{X}$ 到 $\mathbb{R}$ 的函数分布

观测值

![](img/f01928df50903c99ce023dd3c527a33d_961_0.png)

## 高斯过程后验

$\mathcal{GP}$ : 从 $\mathcal{X}$ 到 $\mathbb{R}$ 的函数分布

给定观测值的后验 $\mathcal{GP}$

![](img/f01928df50903c99ce023dd3c527a33d_962_0.png)

## GP 的预测分布

给定：输入 $x_i$，噪声输出 $y_i$

- 核矩阵：$[K]_{x_i x_j} = k(x_i, x_j)$
- 核向量：$k(x^*) = [k(x_1, x^*), \dots, k(x_N, x^*)]^T$

## GP 后验分布：

- 我们可以评估未见数据点 $x'$ 的均值和方差

$\mu(x') = k_{x'}^T(K + \sigma_y^2 I)^{-1}y$

$\sigma^2(x') = k(x', x') + \sigma_y^2 - k_{x'}^T(K + \sigma_y^2 I)^{-1}k_{x'}$

## 观测值：

- 均值对应岭回归 (Kernel Ridge Regression)
- 可以表示偶然不确定性 (aleatoric) 和认知不确定性 (epistemic)

![](img/f01928df50903c99ce023dd3c527a33d_963_0.png)

正弦数据示例（绿色：真实函数；蓝色：噪声数据；红色：GPR 预测均值；阴影：$\pm\sigma$）

## 使用采集函数的 BO 

对于每一轮 $t$：

1. 选择使采集函数 $\text{acq}_t(\theta)$ 最大化的 $\theta_t \in \mathcal{X}$
2. 观测奖励 $r_t = g(\theta_t) + \epsilon_t$

$T$ 轮后：推荐解 $\theta_T^*$

## 采集函数

- 纯探索：仅最终结果
- 改进概率 (PI)
- 期望改进 (EI)
- 探索/利用平衡：中间结果也应该是好的
- 高斯过程置信边界 (GP-UCB)

没有绝对胜者，但文献中有很多...

- 当前的 SOTA：预测熵搜索 (Predictive Entropy Search)

## 改进概率 (PI)

**纯探索：**只关注最终结果

- 令 $g^*_{t-1} = \max(g(\theta_1), \dots, g(\theta_{t-1}))$ 为目前为止的最大值
- 在位置 $x$ 处的改进概率：$PI_t(\theta) = \text{Pr}[g(\theta) \geq g_{t}^*]$

**属性：**

- 可以很容易地为 GP 计算
- 不考虑改进的幅度
- 假设无噪声设置

## 示意图

示例：

![](img/f01928df50903c99ce023dd3c527a33d_967_0.png)

![](img/f01928df50903c99ce023dd3c527a33d_967_1.png)

![](img/f01928df50903c99ce023dd3c527a33d_967_2.png)

![](img/f01928df50903c99ce023dd3c527a33d_967_3.png)

## 期望改进

- 同样考虑改进的幅度
- 使用函数 $g$ 在位置 $x$ 处的改进：$I_t(g, \theta) = \max(g(\theta) - g_{t-1}^*, 0)$

由于 $g$ 未知，我们可以估计期望改进：

$EI_t(\theta) = \mathbb{E}_{g \sim GP(\mathcal{D})}[I_t(\theta)|\mathcal{D}]$,其中 $\mathcal{D} = [\theta_1, g_1, \dots, \theta_{t-1}, g_{t-1}]$

- 同样可以为 GP 进行估计，效果比改进概率 (PI) 好
- 有一个超参数 $\xi$ 可以缩放探索
- $\xi$ 总是加到 $g_{t-1}^*$，假装我们找到了更高的最大值
- 强制探索

## 高斯过程置信边界

- 面对不确定性时的乐观
