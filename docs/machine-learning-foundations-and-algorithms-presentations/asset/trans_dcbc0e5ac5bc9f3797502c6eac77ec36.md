

## 关于贝叶斯优化的更多内容

- UCB 有理论结果：在 $g$ 的某些平滑性假设下，最终可以找到最优解。
- 基于纯探索的方法方法尚不存在此类结果。

![](img/f01928df50903c99ce023dd3c527a33d_978_0.png)

## 选择协方差

- 高斯过程 (GP) 覆盖的函数空间取决于 $k(\theta, \theta')$
- 平方指数（高斯）核

```
$k_{SE}(\theta, \theta') = \exp \left( -\frac{\sum_{i=1}^{n}(\theta_i - \theta'_i)^2}{2\rho_i^2} \right)$
```

- 如果对于每个维度 $i$，$\rho_i = \rho$，则是各向同性的，否则为各向异性。
- 由高斯核定义的函数通常太平滑。

## Matern 协方差

- 使用显式参数 $\nu$ 来控制平滑度
- Matérn 核：
$$k_{\nu}(\mathbf{x}, \mathbf{x}') = \frac{2^{1-\nu}}{\Gamma(\nu)} \left(\sqrt{2\nu}r^2(\mathbf{x}, \mathbf{x}')\right)^{\nu} K_{\nu} \left(\sqrt{2\nu}r^2(\mathbf{x}, \mathbf{x}')\right)$$
$$k_{5/2}(\mathbf{x}, \mathbf{x}') = \left(1 + \sqrt{5}r^2(\mathbf{x}, \mathbf{x}') + \frac{5}{3}r^2(\mathbf{x}, \mathbf{x}')\right) \exp \left(-\sqrt{5}r^2(\mathbf{x}, \mathbf{x}')\right)$$
$$\text{with} \ r^2(\mathbf{x}, \mathbf{x}') = \sum_{i=1}^{n}(x_i - x'_i)^2/\rho_i^2$$
- $\Gamma$: Gamma 函数
- $K_{\nu}$: 第二类贝塞尔函数

当 $\nu \to \infty$ 时，Matérn 核收敛于高斯核。

## 协方差比较：后验概率

![](img/f01928df50903c99ce023dd3c527a33d_981_0.png)
![](img/f01928df50903c99ce023dd3c527a33d_981_1.png)
![](img/f01928df50903c99ce023dd3c527a33d_981_2.png)
![](img/f01928df50903c99ce023dd3c527a33d_981_3.png)

图 4.1：面板 (a)：协方差函数；(b)：从具有 Matérn 协方差函数（等式 4.14）的高斯过程中抽取的随机函数，对应不同的 $\nu$ 值且 $\ell=1$。右侧的样本函数是通过对 x 轴进行 2000 个等距点离散化得到的。

## 协方差超参数

- GP 有其自己的需要调优的超参数 $\gamma$（核参数 $\rho$，噪声方差 $\sigma$）
- 影响后验概率，因此也影响采集函数

![](img/f01928df50903c99ce023dd3c527a33d_982_0.png)
![](img/f01928df50903c99ce023dd3c527a33d_982_1.png)

## 选择协方差超参数

**a) 在高斯过程中优化边际似然：**

$\gamma^* = \text{argmax}_\gamma \log p(\mathbf{r}_{1:t}|\boldsymbol{\theta}_{1:t}, \gamma, \sigma)$, $\log p(\mathbf{r}_{1:t}|\boldsymbol{\theta}_{1:t}, \gamma, \sigma) = -\frac{1}{2}\mathbf{r}_{1:t}^T(\mathbf{K}_{\gamma} + \sigma\mathbf{I})^{-1}\mathbf{r}_{1:t} - \frac{1}{2}\log|\mathbf{K}_{\gamma} + \sigma\mathbf{I}| - \frac{t}{2}\log 2\pi$

- 可以通过梯度下降完成
- 对超参数使用单点估计。

**b) 采集函数中的贝叶斯处理**

- 对超参数进行积分
- $acq_t(\boldsymbol{\theta}) = \int acq_t(\boldsymbol{\theta}, \gamma, \sigma)p(\gamma, \sigma|\mathbf{r}_{1:t}, \boldsymbol{\theta}_{1:t})d\gamma,\sigma$
- 可以使用蒙特卡洛马尔可夫链（MCMC）采样进行近似
- 效果往往更好，但计算代价大得多。

## 积分期望改进

## 积分 EI

![](img/f01928df50903c99ce023dd3c527a33d_984_0.png)
![](img/f01928df50903c99ce023dd3c527a33d_984_1.png)

## 典型应用：超参数优化

- 优化超参数（特定层学习率、权重衰减以及针对 CIFAR-10 的 CNN）
- 每次函数评估耗时约 1 小时
- 人类专家 Alex Krizhevsky
![](img/f01928df50903c99ce023dd3c527a33d_985_0.png)

## 示例：AlphaGo 中的贝叶斯优化

- 在 AlphaGo 开发期间，其许多超参数经过了多次贝叶斯优化。例如，在与 Lee Sed 对战之前，他们调优了最新的 AlphaGo 代理，这使其自对弈胜率从 50% 提高到 66.5%。这个调优版本被部署在了决赛中。

## 黑盒之外的超参数优化

![](img/f01928df50903c99ce023dd3c527a33d_987_0.png)

## 多保真度优化

- 使用与黑盒性能相关的廉价近似来替代黑盒，例如：
  - 数据子集
  - 较少的迭代次数（如 SGD）
  - 深度学习中较少的试验
  - 目标识别中的采样图像
- 也适用于其他领域，例如流体仿真：
  - 较少的粒子
  - 更短的仿真

## 多保真度优化

使用低保真度评估
- 例如：数据子集（此处为 MNIST 的 SVM）
![](img/f01928df50903c99ce023dd3c527a33d_989_0.png)
- 在小子子集上大量廉价评估
- 在全数据集上少量昂贵评估
- 速度提升高达 100 倍 [Klein 等人，2017]

## 多保真度优化（重复标题）

- 例如：数据子集（此处为 MNIST 的 SVM）
![](img/f01928df50903c99ce023dd3c527a33d_990.png)
- 子集大小（MNIST）
- 拟合高斯过程模型 $f(\lambda,b)$，预测性能作为超参数 $\lambda$ 和预算 $b$ 的函数
- 选择 $\lambda$ 和预算 $b$ 以实现性价比最大化

## 更简单的方法：连续减半 (Successive Halving, SH)

[Jamieson & Talwalkar, AISTATS 2016]
![](img/f01928df50903c99ce023dd3c527a33d_991_0.png)

- 从大量的超参数配置开始，分配小预算
- 为最佳“K”超参数（如 Half）扩展预算。

## Hyperband

![](img/f01928df50903c99ce023dd3c527a33d_992_0.png)
![](img/f01928df50903c99ce023dd3c527a33d_992_1.png)
![](img/f01928df50903c99ce023dd3c527a33d_992_2.png)

**问题：** 对于给定的预算 B，我们应该使用多少配置？

- **包络 (Envelope)：**
  - 显示到最终评估误差（阴影区域）
  - 只有当阴影区域不再重叠时才能区分两种配置
  - 通常情况下，阴影区域的大小是知的
- **Hyperband：**
  - 使用不同的初始预算多次运行连续半。

## Hyperband（其前 4 次调用）

![](img/f01928df50903c99ce023dd3c527a33d_993_0.png)

## BOHB：贝叶斯优化与 Hyperband

Hyperband 的优势
- 强力的任意性能
- 通用性
  - 低维连续空间
  - 带有条件、分类维度等的高维空间
- 易于实现
- 可扩展
- 易于并行化

## 贝叶斯优化的优势：强大的最终性能

在 BOHB 中结合两者的优点
- 贝叶斯优化
  - 用于选择待评估配置（使用 TPE 变体）
- Hyperband
  - 用于决定如何分配预算

[Falkner, Klein & Hutter, ICML 2018]

## Hyperband vs 随机搜索

## 最大的优势：大幅提升的任意性能

adult 数据上的 Auto-Net

## 贝叶斯优化 vs 随机搜索

![](img/f01928df50903c99ce023dd3c527a33d_996_0.png)

**最大的优势：大幅提升的最终性能**

adult 数据上的 Auto-Net
Gerhard Neumann | Maschin Lernen | KIT | SS 2024

## 结合贝叶斯优化与 Hyperband

![](img/f01928df50903c99ce023dd3c527a33d_997_0.png)

## 两者的结合：强力的任意和最终性能

adult 数据上的 Auto-Net
Gerhard Neumann | Maschin Lernen | KIT | SS 2024

## 总结

**贝叶斯优化：**

- 用于学习适应函数的贝叶斯处理
- 包含了模型不确定性（例如高斯过程）
- 使用采集函数来引导探索
  - 生成具有高模型不确定性的样本
  - ……以及可能的高回报
- 对超参数的处理有帮助。

**黑盒之外：**

- 使用多保真度/预算
- Hyperband 与 BO 的结合可以将超参数优化速度提升高达 50 倍

