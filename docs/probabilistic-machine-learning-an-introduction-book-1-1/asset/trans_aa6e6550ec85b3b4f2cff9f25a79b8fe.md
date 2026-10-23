

## 7 贝叶斯统计

### 7.1 引言

在第 4 章中，我们讨论了如何从数据中估计参数。然而，这忽略了对估计值的不确定性，而这对某些应用程序来说可能很重要。在本章中，我们通过计算给定数据下的参数后验分布来对我们的不确定性进行建模：

$p(\boldsymbol{\theta}|\mathcal{D}) = \frac{p(\boldsymbol{\theta})p(\mathcal{D}|\boldsymbol{\theta})}{p(\mathcal{D})} = \frac{p(\boldsymbol{\theta})p(\mathcal{D}|\boldsymbol{\theta})}{\int p(\boldsymbol{\theta}')p(\mathcal{D}|\boldsymbol{\theta}')d\boldsymbol{\theta}'}$ (7.1)

这在概念上与我们在第 2 章中讨论的概率推断相似，不过在本章中，我们将把推断应用于更“标准”的模型类型。

#### 7.1.1 计算后验分布

贝叶斯推断依赖于计算公式 (7.1) 中的后验分布的能力。由于需要计算分母中的积分，这在计算上可能很困难；这一项是必要的，以确保分布在整个空间上积分为 1。

在第 7.2 节中，我们将讨论一类可以以封闭形式计算该积分的模型。这些模型通常用作更复杂模型的“构建模块”。然而，一般来说，我们需要使用第 7.7 节中讨论的一些算法来近似后验分布。

#### 7.1.2 概括后验分布

后验分布（通常）是一个高维对象，难以可视化和处理。在本节中，我们将讨论一些概括后验分布的常见方法。

##### 7.1.2.1 点估计

对后验分布所做的最简单的事情就是将其“压缩”到一个单点，这可以解释为我们对未知参数的“最佳猜测”。这被称为点估计。如我们在第 8.1.5 节中讨论的那样，最优的点估计最小化后验期望损失：

$\hat{\boldsymbol{\theta}} = \arg\min_{\boldsymbol{\theta}} \int p(\boldsymbol{\theta}|\mathcal{D})\ell(\boldsymbol{\theta},\hat{\boldsymbol{\theta}})d\boldsymbol{\theta}$ (7.2)

其中 $\ell(\boldsymbol{\theta}, \hat{\boldsymbol{\theta}})$ 是当真实值是 $\boldsymbol{\theta}$ 但我们猜测 $\hat{\boldsymbol{\theta}}$ 时产生的损失。

如果我们使用 $\ell_2$ 损失，$\ell(\boldsymbol{\theta}, \hat{\boldsymbol{\theta}}) = \|\boldsymbol{\theta} - \hat{\boldsymbol{\theta}}\|_2^2$，则最优估计是后验均值，$\bar{\boldsymbol{\theta}} = \mathbb{E}[\boldsymbol{\theta}|\mathcal{D}]$，如我们在第 8.1.5.1 节中所示。如果我们使用 $\ell_1$ 损失，$\ell(\boldsymbol{\theta}, \hat{\boldsymbol{\theta}}) = |\boldsymbol{\theta} - \hat{\boldsymbol{\theta}}|_1$，则最优估计是后验中位数，如我们在第 8.1.5.2 节中所示。如果我们使用 0-1 损失，$\ell(\boldsymbol{\theta}, \hat{\boldsymbol{\theta}}) = \mathbb{I}\left(\boldsymbol{\theta} = \hat{\boldsymbol{\theta}}\right)$，则最优估计是后验众数或最大后验（MAP）估计，$\hat{\boldsymbol{\theta}} = \operatorname{argmax}_{\boldsymbol{\theta}} p(\boldsymbol{\theta}|\mathcal{D})$，如我们在第 8.1.2.1 节中所示。这是最容易计算的点估计，因为它只需要优化，而不需要积分。然而，对于实值向量的参数估计来说，0-1 损失是一种非常不自然的损失函数。

##### 7.1.2.2 可信区间

我们通常需要对参数估计值有一个置信度量。对于某个（标量）量 $\theta$，一个标准的置信度量是其后验分布的“宽度”。这可以使用 $100(1 - \alpha)\%$ **可信区间**来衡量，它是一个（连续的）区域 $C = (\ell, u)$（代表下限和上限），其中包含 $1 - \alpha$ 的后验概率质量，即

$C_{\alpha}(\mathcal{D}) = (\ell, u) : P(\ell \le \theta \le u|\mathcal{D}) = 1 - \alpha$ \tag{7.3}

可能有许多区间满足公式 (7.3)，因此我们通常选择一个使得每个尾部有 $(1 - \alpha)/2$ 质量的区间；这被称为**中央区间**。如果后验具有已知的函数形式，我们可以使用 $\ell = F^{-1}(\alpha/2)$ 和 $u = F^{-1}(1 - \alpha/2)$ 计算后验中央区间，其中 $F$ 是后验的累积分布函数（cdf），$F^{-1}$ 是逆累积分布函数。例如，如果后验是高斯分布，$p(\theta|\mathcal{D}) = \mathcal{N}(0,1)$，且 $\alpha = 0.05$，那么我们有 $\ell = \Phi^{-1}(\alpha/2) = -1.96$，且 $u = \Phi^{-1}(1 - \alpha/2) = 1.96$，其中 $\Phi$ 表示高斯分布的 cdf。这在图 3.6b 中进行了说明。这证明了常见的以 $\mu \pm 2\sigma$ 形式引用可信区间的做法，其中 $\mu$ 代表后验均值，$\sigma$ 代表后验标准差，而 $2$ 是 $1.96$ 的一个良好近似值。

一般来说，计算后验的逆 cdf 往往很困难。在这种情况下，一种简单的替代方法是从后验中抽取样本，然后使用后验分位数的蒙特卡洛近似：我们只需对 $S$ 个样本进行排序，并找到在排序列表中位于 $\alpha/S$ 位置的那个样本。当 $S \to \infty$ 时，这收敛到真实分位数。有关此操作的演示，请参见 `beta_credible_int_demo.py`。

中央区间的一个问题是，中央区间外部可能存在比内部点具有更高概率的点，如图 7.1(a) 所示。这促使了一种称为**最高后验密度**或 **HPD** 区域的替代量，它是概率高于某个阈值的点的集合。更准确地说，我们在 pdf 上找到阈值 $p^*$，使得

$1 - \alpha = \int_{\theta: p(\theta|\mathcal{D}) > p^*} p(\theta|\mathcal{D}) d\theta$ \tag{7.4}

然后定义 HPD 为

$C_{\alpha}(\mathcal{D}) = \{\theta : p(\theta|\mathcal{D}) \ge p^*\}$ \tag{7.5}

1.  可信区间与置信区间不同，后者是我们在附录 E.3.4 中讨论的频率学统计中的一个概念。

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_205_0.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_205_1.png)

图 7.1: (a) Beta(3,9) 后验的中央区间和 (b) HPD 区域。CI 为 (0.06, 0.52)，HPD 为 (0.04, 0.48)。改编自 [Hof09] 中的图 3.6。由 betaHPD.m 生成。

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_205_2.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_205_3.png)

图 7.2: (a) 假设的多模态后验的中央区间和 (b) HPD 区域。改编自 [Gel+04] 中的图 2.2。由 postDensityIntervals.m 生成。

在一维情况下，HPD 区域有时被称为最高密度区间或 HDI。例如，图 7.1(b) 显示了 Beta(3,9) 分布的 95% HDI，即 (0.04, 0.48)。我们看到，尽管它仍然包含 95% 的质量，但它比中央区间更窄；此外，其内部的每个点都比外部的每个点具有更高的密度。

对于单模分布，HDI 将是围绕众数的包含 95% 质量的最窄区间。为了理解这一点，想象“注水”的反向过程，我们降低水位，直到 95% 的质量显露出来，而只有 5% 被淹没。这提供了一种在一维情况下计算 HDI 的简单算法：只需搜索使得区间包含 95% 质量且宽度最小的点。如果我们知道分布的逆 CDF，可以通过一维数值优化来完成；或者如果我们有一袋样本，可以通过搜索排序后的数据点来完成（参见 betaHPD.m 进行演示）。

如果后验是多模的，HDI 甚至可能不是一个连通区域：参见图 7.2(b) 的示例。然而，概括多模态后验总是很困难的。

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_206_0.png)

*图 7.3:* 计算 $z = y^2$ 的分布，其中 $p(y)$ 是均匀的（左）。解析结果展示在中间，蒙特卡洛近似展示在右侧。由 `change_of_vars_demo1d.py` 生成。

##### 7.1.2.3 后验样本

通常，我们需要计算随机变量某个函数的期望值，$Z = f(Y)$。我们可以通过从其（后验）分布中绘制许多 $Y$ 的样本来近似这个值，然后使用

$$\mathbb{E}[f(Y)] = \int f(y)p(y)dy \approx \frac{1}{S}\sum_{s=1}^{S} f(y_s) \tag{7.6}$$

这被称为**蒙特卡洛积分**，与数值积分（基于在固定网格点上评估函数）相比，其优势在于函数只在具有不可忽略概率的地方进行评估。因此，MC 积分在扩展到高维问题时表现更好。

例如，假设 $y \sim \text{Unif}(-1,1)$ 且 $z = f(y) = y^2$。精确均值由下式给出

$$\mathbb{E}[z] = \int_{-1}^{1} \frac{1}{2} y^2 dy = \frac{1}{2}\left[\frac{y^3}{3}\right]_{-1}^{1} = 1/3 \tag{7.7}$$

我们可以通过从 $p(y)$ 中绘制许多样本，将它们平方，然后取平均值来近似这个值；我们发现 $\mathbb{E}[\hat{f}] = 0.34$，如图 7.3 所示。

通过改变函数 $f$，我们可以近似许多感兴趣的量，例如均值，

