

![](img/ca72c1626f4850f058a9edc138c1ac73_724_0.png)

图 18.8: 使用相同核函数的核岭回归（KRR）与高斯过程回归（GPR）的比较。由 krr_vs_gpr.ipynb 生成。

对 \(\alpha\) 求最小化可得 \(\hat{\alpha} = (\mathbf{K} + \sigma_y^2 \mathbf{I})^{-1} \mathbf{y}\)，这与公式 (18.57) 相同。此外，测试点的预测为 \(\hat{f}(x_*) = k_*^T \alpha = k_*^T (\mathbf{K} + \sigma_y^2 \mathbf{I})^{-1} \mathbf{y}\) (18.98)。这被称为核岭回归 [Vov13]。可以看到，结果与公式 (18.55) 中 GP 的后验预测均值匹配。

### 18.3.7.4 KRR 与 GPR 的示例

在本节中，我们在一个简单的一维问题上比较 KRR 与 GP 回归。由于底层函数被认为是周期性的，我们使用公式 (18.18) 中的周期性核。为了捕捉观测值含噪这一事实，我们在此基础上添加一个 **白噪声核** \(\mathcal{K}(x, x') = \sigma_y^2 \delta(x - x')\) (18.99)。

如同公式 (18.48)。因此有 3 个 GP 超参数：核长度尺度 \(\ell\)、核周期性 \(p\) 和噪声水平 \(\sigma_y^2\)。我们可以通过使用梯度下降最大化边缘似然来优化这些参数（参见第 18.6.1 节）。对于 KRR，我们也有 3 个超参数（\(\ell, p\) 和 \(\lambda = \sigma_y^2\)）；我们使用网格搜索结合交叉验证来优化这些参数（通常比基于梯度的优化慢）。得到的模型拟合如图 18.8 所示，且非常相似，这与预期一致。

## 18.4 具有非高斯似然的 GPs

迄今为止，我们一直专注于使用高斯似然的 GP 回归。在这种情况下，后验也是一个 GP，所有计算都可以解析地执行。然而，如果似然是非高斯的，我们就无法再精确计算后验了。我们可以通过改变似然的形式来创建各种不同的“经典”模型，如表 18.1 所示。在下面的节中，我们简要讨论一些近似推断方法。（有关更多详细信息，见例如 [WSS21]。）

| 模型 | 似然 | 第 18.3.2 节 |
|---|---|---|
| 回归 | $\mathcal{N}(f_i, \sigma_y^2)$ | 第 18.3.2 节 |
| 鲁棒回归 | $\mathcal{T}_\nu(f_i, \sigma_y^2)$ | 第 18.4.4 节 |
| 二分类 | Ber\((\sigma(f_i))\) | 第 18.4.1 节 |
| 多类分类 | Cat(softmax\((\mathbf{f}_i)\)) | 第 18.4.2 节 |
| 泊松回归 | Poi\((\exp(f_i))\) | 第 18.4.3 节 |

表 18.1: 具有多种似然的 GP 模型摘要。

| log p(y_i|f_i) | \(\frac{\partial}{\partial f_i} \log p(y_i|f_i)\) | \(\frac{\partial^2}{\partial f_i^2} \log p(y_i|f_i)\) |
|---|---|---|
| \(\log \sigma(y_i f_i)\) | \(t_i - \pi_i\) | \(-\pi_i(1 - \pi_i)\) |
| \(\log \Phi(y_i f_i)\) | \(\frac{y_i \phi(f_i)}{\Phi(y_i f_i)}\) | \(-\frac{\phi_i^2}{\Phi(y_i f_i)^2} - \frac{y_i f_i \phi(f_i)}{\Phi(y_i f_i)}\) |

表 18.2: 二分类 logistic/probit GP 回归的似然、梯度和 Hessian。我们假设 \(y_i \in \{-1,+1\}\)，并定义 \(t_i = (y_i+1)/2 \in \{0,1\}\)，对于 logistic 回归 \(\pi_i = \sigma(f_i)\)，对于 probit 回归 \(\pi_i = \Phi(f_i)\)。此外，\(\phi\) 和 \(\Phi\) 是 \(\mathcal{N}(0,1)\) 的 pdf 和 cdf。来源：[RW06, p43]。

### 18.4.1 二分类

在本节中，我们考虑使用 GPs 进行二分类。如果使用 sigmoid 链接函数，则 \(p(y_n=1|\mathbf{x}_n) = \sigma(y_n f(\mathbf{x}_n))\)。如果假设 \(y_n \in \{-1,+1\}\)，则 \(p(y_n|\mathbf{x}_n) = \sigma(y_n f_n)\)，因为 \(\sigma(-z) = 1 - \sigma(z)\)。如果使用 probit 链接，则 \(p(y_n=1|\mathbf{x}_n) = \Phi(y_n f(\mathbf{x}_n))\)，其中 \(\Phi(z)\) 是标准正态分布的 cdf。更一般地，设 \(p(y_n|\mathbf{x}_n) = \text{Ber}(y_n|\varphi(f_n))\)。整体 log joint 的形式为

$$
\mathcal{L}(\mathbf{f}_X) = \log p(\mathbf{y}|\mathbf{f}_X) + \log p(\mathbf{f}_X|\mathbf{X}) \tag{18.100}
$$
$$
= \log p(\mathbf{y}|\mathbf{f}_X) - \frac{1}{2} \mathbf{f}_X^T \mathbf{K}_{X,X}^{-1} \mathbf{f}_X - \frac{1}{2} \log |\mathbf{K}_{X,X}| - \frac{N}{2} \log 2\pi \tag{18.101}
$$

近似推断的最简单方法是使用 Laplace 近似（第 7.4.3 节）。log joint 的梯度和 Hessian 如下

$$
\nabla \mathcal{L} = \nabla \log p(\mathbf{y}|\mathbf{f}_X) - \mathbf{K}_{X,X}^{-1} \mathbf{f}_X \tag{18.102}
$$
$$
\nabla^2 \mathcal{L} = \nabla^2 \log p(\mathbf{y}|\mathbf{f}_X) - \mathbf{K}_{X,X}^{-1} = -\mathbf{\Lambda} - \mathbf{K}_{X,X}^{-1} \tag{18.103}
$$

其中 \(\mathbf{\Lambda} \triangleq -\nabla^2 \log p(\mathbf{y}|\mathbf{f}_X)\) 是一个对角矩阵，因为似然在样本间分解。logit 和 probit 情况下 log 似然的梯度和 Hessian 表达式如表 18.2 所示。收敛时，后验的 Laplace 近似采用以下形式：

$$
p(\mathbf{f}_X|\mathcal{D}) \approx q(\mathbf{f}_X) = \mathcal{N}(\hat{\mathbf{f}}, (\mathbf{K}_{X,X}^{-1} + \mathbf{\Lambda})^{-1}) \tag{18.104}
$$

其中 \(\hat{\mathbf{f}}\) 是 MAP 估计。有关更多详细信息，请参见 [RW06, Sec 3.4]。为了提高精度，我们可以使用变分推断，在此假设 \(q(\mathbf{f}_X) = \mathcal{N}(\mathbf{f}_X|\mathbf{m}, \mathbf{S})\)；然后我们使用（随机）梯度下降优化 \(\mathbf{m}\) 和 \(\mathbf{S}\)，而不是假设 \(\mathbf{S}\) 是众点处的 Hessian。详情请参见第 18.5.4 节。

![](img/ca72c1626f4850f058a9edc138c1ac73_726_0.png)

图 18.9: 由带 SE 核的 GP 生成的二分类器的后验预测概率轮廓。（a）手动核参数：短长度尺度，\(\ell = 0.5\)，方差 \(3.16^2 \approx 9.98\)。（b）学习到的核参数：长长度尺度，\(\ell = 1.19\)，方差 \(4.79^2 \approx 22.9\)。由 `gpc_demo_2d.ipynb` 生成。

一旦我们有了高斯后验 \(q(\mathbf{f}_X|\mathcal{D})\)，然后就可以使用标准 GP 预测来计算 \(q(f_*|\mathbf{x}_*,\mathcal{D})\)。最后，我们可以使用以下公式近似二进制标签的后验预测分布：

\(\pi_* = p(y_*=1|\mathbf{x}_*,\mathcal{D}) = \int p(y_*=1|f_*)q(f_*|\mathbf{x}_*,\mathcal{D})df_*\) (18.105)

这个一维积分可以使用第 15.3.6 节中的 probit 近似来计算。在这种情况下，\(\pi_* \approx \sigma(\kappa(v)\mathbb{E}[f_*])\)，其中 \(v = \mathbb{V}[f_*]\) 且 \(\kappa^2(v) = (1 + \pi v/8)^{-1}\)。

在图 18.9 中，我们展示了一个 2D 的合成二分类问题。我们使用 SE 核。左侧，我们展示了使用手动设置的超参数的预测；我们使用短长度尺度，因此决策边界有非常剧烈的转折。右侧，我们展示了使用学习到的超参数的预测；模型倾向于对数据给出更简洁的解释。

### 18.4.2 多类分类

多类情况稍微困难一些，因为函数现在需要返回一个 \(C\) 维 logits 向量才能得到 \(p(y_n|\mathbf{x}_n) = \text{Cat}(y_n|\text{softmax}(\mathbf{f}_n))\)，其中 \(\mathbf{f}_n = (f_n^1,\dots,f_n^C)\)。通常假设 \(f^c \sim \text{GP}(0,\mathcal{K}_c)\)。因此，我们每个类有一个潜在函数，它们先验上相互独立，并且可能使用不同的核。

我们可以按照 [RW06, Sec 3.5] 中讨论的方法为该模型推导 Laplace 近似。或者，我们可以使用变分方法，利用 [Cha12] 中多项式 softmax 的局部变分下界。另一种基于辅助变量数据增广的变分方法在 [Wen+19b; Liu+19a; GFW020] 中有所描述。

![](img/ca72c1626f4850f058a9edc138c1ac73_727_0.png)

图 18.10: 带 GP 的泊松回归。（a）观测数据（黑色点）和真实对数速率函数（黄色线）。（b）MCMC 得到的后验预测分布（阴影显示 1 和 2 \(\sigma\) 带）。（c）SVI 得到的后验预测分布。由 gp_poisson_1d.ipynb 生成。

### 18.4.3 泊松回归的 GPs（Cox 过程）

本节中说明了泊松回归，其中底层对数速率函数由 GP 建模。这被称为 Cox 过程。我们可以在此模型中使用 Laplace、MCMC 或 SVI（随机变分推断）进行近似后验推断。在图 18.10 中，我们给出了一个一维示例，其中使用 Matèrn \(\frac{5}{2}\) 核。我们应用了 MCMC 和 SVI。在 VI 情况下，我们还需要指定后验的形式；我们对变分 GP 后验 \(p(f|\mathbf{X}, \mathbf{y})\) 使用高斯近似，对核参数使用点估计。

一个有趣的应用是空间疾病制图。例如，[VPV10] 讨论了在芬兰不同地区建模心脏病发作相对风险的问题。数据包括 1996–2000 年芬兰的心脏病发作，聚合为 20km \(\times\) 20km 网格单元。似然的形式如下：\(y_n \sim \text{Poi}(e_n r_n)\)，其中 \(e_n\) 是已知的预期死亡人数（与单元 \(n\) 的人口和总体死亡率相关），\(r_n\) 是我们要推断的单元 \(n\) 的 **相对风险**。由于数据计数较小，我们通过与空间邻居共享信息来对问题进行正则化。因此，我们假设 \(f \triangleq \log(r) \sim \text{GP}(0, \mathcal{K})\)。我们使用 \(\nu = 3/2\) 的 Matèrn 核（第 18.2.1.3 节），以及从数据估计的长度尺度和幅度。

图 18.11 展示了该方法的一个应用示例（使用 Laplace 近似）。左侧，我们绘制了后验平均相对风险（RR）；右侧，则是后验方差。我们发现，RR 在芬兰东部较高，这与其他研究一致。我们还发现，北部的方差较高，因为那里居住的人较少。

### 18.4.4 其他似然

存在许多其他似然。例如，[VJV09] 使用 Student \(t\) 似然来进行鲁棒回归。[WSS21] 讨论了一种用于在具有此类非共轭似然的 GPs 中执行近似变分推断的通用方法。

