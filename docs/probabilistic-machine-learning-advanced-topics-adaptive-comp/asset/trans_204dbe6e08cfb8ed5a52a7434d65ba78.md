

其逆函数是分位数函数

$$F^{-1}(p) = -\frac{\ln(1-p)}{\lambda}$$ (11.15)

根据上述定理，如果 \( U \sim \text{Unif}(0,1) \)，我们知道 \( F^{-1}(U) \sim \text{Expon}(\lambda) \)。因此，我们可以通过先从均匀分布中采样，然后使用 \(-\ln(1-u)/\lambda\) 变换结果来从指数分布中采样。（事实上，由于 \( 1-U \sim \text{Unif}(0,1) \)，我们可以直接使用 \(-\ln(u)/\lambda$。）

### 11.3.2 从高斯分布中采样（Box-Muller 方法）

在本节中，我们描述了一种从高斯分布中采样的方法。其思路是从单位半径圆中均匀采样，然后利用变量代换公式推导球形二维高斯分布的样本。这可以看作是来自一维高斯分布的两个样本。
更详细地说，均匀采样 \( z_1, z_2 \in (-1, 1) \)，然后丢弃不满足 \( z_1^2 + z_2^2 \le 1 \) 的点对。结果将是单位圆内均匀分布的点，因此 \( p(\mathbf{z}) = \frac{1}{\pi}\mathbb{I}(z \text{ inside circle}) \)。现在定义

$$x_i = z_i \left( \frac{-2 \ln r^2}{r^2} \right)^{\frac{1}{2}}$$ (11.16)

对 \( i = 1 : 2 \)，其中 \( r^2 = z_1^2 + z_2^2 \)。使用多元变量代换公式，我们有

$$p(x_1, x_2) = p(z_1, z_2) \left| \frac{\partial(z_1, z_2)}{\partial(x_1, x_2)} \right| = \left[ \frac{1}{\sqrt{2\pi}} \exp(-\frac{1}{2}x_1^2) \right] \left[ \frac{1}{\sqrt{2\pi}} \exp(-\frac{1}{2}x_2^2) \right]$$ (11.17)

因此 \( x_1 \) 和 \( x_2 \) 是来自一元高斯分布的两个独立样本。这被称为 Box-Muller 方法。

要从多元高斯分布中采样，我们首先计算其协方差矩阵的 Cholesky 分解，\( \mathbf{\Sigma} = \mathbf{L}\mathbf{L}^\top \)，其中 \( \mathbf{L} \) 为下三角矩阵。接着，我们使用 Box-Muller 方法采样 \( \mathbf{x} \sim \mathcal{N}(\mathbf{0}, \mathbf{I}) \)。最后，我们设置 \( \mathbf{y} = \mathbf{Lx} + \boldsymbol{\mu} \)。这是成立的，因为

$$\text{Cov}[\mathbf{y}] = \mathbf{L}\text{Cov}[\mathbf{x}]\mathbf{L}^\top = \mathbf{L}\mathbf{I}\mathbf{L}^\top = \mathbf{\Sigma}$$ (11.18)

## 11.4 拒绝采样

假设我们想要从目标分布中采样

$$p(\mathbf{x}) = \tilde{p}(\mathbf{x}) / Z_p$$ (11.19)

其中 \( \tilde{p}(\mathbf{x}) \) 是未归一化版本，而

$$Z_p = \int \tilde{p}(\mathbf{x}) \, d\mathbf{x}$$ (11.20)

是（可能未知的）归一化常数。解决此问题的最简单方法之一是拒绝采样，我们将对此进行解释。

![](img/ca72c1626f4850f058a9edc138c1ac73_513_0.png)

图 11.4：(a) 拒绝采样的示意图。引自 [And+03] 的图 2。经 Nando de Freitas 友好许可使用。(b) 从 Ga($\alpha=5.7, \lambda=2$) 分布（实蓝色）中进行拒绝采样，使用形式为 $M \text{Ga}(k, \lambda-1)$（虚红色）的建议分布，其中 $k=[5.7]=5$。曲线在 $\alpha-k=0.7$ 处相切。由 rejection_sampling_demo.ipynb 生成。

### 11.4.1 基本思路

在拒绝采样中，我们需要访问一个 **建议分布** $q(\boldsymbol{x})$，其满足某个常数 $C$ 的 $C q(\boldsymbol{x}) \ge \tilde{p}(\boldsymbol{x})$。函数 $C q(\boldsymbol{x})$ 为 $\tilde{p}$ 提供了一个上包络。

我们可以利用建议分布从目标分布中生成样本，如下所示。我们首先采样 $\boldsymbol{x}_0 \sim q(\boldsymbol{x})$，这相当于选择一个随机的 $\boldsymbol{x}$ 位置，然后采样 $u_0 \sim \text{Unif}(0, C q(\boldsymbol{x}_0))$，这相当于在包络下选择一个随机高度（$y$ 位置）。如果 $u_0 > \tilde{p}(\boldsymbol{x}_0)$，则拒绝该样本，否则接受它。该过程在 1d 中如图 11.4(a) 所示：接受区域以阴影表示，拒绝区域是阴影区域与上包络之间的白色区域。

我们现在证明此程序的正确性。首先，要注意给定样本 $\boldsymbol{x}_0$ 被接受的概率等于样本 $u_0 \sim \text{Unif}(0, C q(\boldsymbol{x}_0))$ 小于或等于 $\tilde{p}(\boldsymbol{x}_0)$ 的概率，即，

$q(\text{accept}|\boldsymbol{x}_0) = \int_0^{\tilde{p}(\boldsymbol{x}_0)} \frac{1}{C q(\boldsymbol{x}_0)} du = \frac{\tilde{p}(\boldsymbol{x}_0)}{C q(\boldsymbol{x}_0)}$ (11.21)

因此

$q(\text{propose and accept } \boldsymbol{x}_0) = q(\boldsymbol{x}_0)q(\text{accept}|\boldsymbol{x}_0) = q(\boldsymbol{x}_0)\frac{\tilde{p}(\boldsymbol{x}_0)}{C q(\boldsymbol{x}_0)} = \frac{\tilde{p}(\boldsymbol{x}_0)}{C}$ (11.22)

对两边积分得

$\int q(\boldsymbol{x}_0)q(\text{accept}|\boldsymbol{x}_0) d\boldsymbol{x}_0 = q(\text{accept}) = \frac{\int \tilde{p}(\boldsymbol{x}_0) d\boldsymbol{x}_0}{C} = \frac{Z_p}{C}$ (11.23)

因此，我们看到接受点的分布由目标分布给出：

$q(\boldsymbol{x}_0|\text{accept}) = \frac{q(\boldsymbol{x}_0, \text{accept})}{q(\text{accept})} = \frac{\tilde{p}(\boldsymbol{x}_0)}{C} \frac{C}{Z_p} = \frac{\tilde{p}(\boldsymbol{x}_0)}{Z_p} = p(\boldsymbol{x}_0)$ (11.24)

该方法效率如何？如果 \(\tilde{p}\) 是归一化的目标分布，则接受概率为 \(1/C\)。因此，我们希望在满足 \(Cq(x) \ge \tilde{p}(x)$ 的前提下选择尽可能小的 \(C$。

### 11.4.2 示例

例如，假设我们想要从伽马分布中采样：3

\(\text{Ga}(x|\alpha, \lambda) = \frac{1}{\Gamma(\alpha)} x^{\alpha-1} \lambda^\alpha \exp(-\lambda x) \quad (11.25)\)

其中 \(\Gamma(\alpha)$ 是伽马函数。可以证明，如果 \(X_i \stackrel{iid}{\sim} \text{Expon}(\lambda)$，且 \(Y = X_1 + \cdots + X_k$，则 \(Y \sim \text{Ga}(k, \lambda)$。对于非整数形状参数 \(\alpha$，我们无法使用此技巧。但是，我们可以使用拒绝采样，使用 \(\text{Ga}(k, \lambda - 1)$ 分布作为建议分布，其中 \(k = \lfloor \alpha \rfloor$。比率形式为

\(\frac{p(x)}{q(x)} = \frac{\text{Ga}(x|\alpha, \lambda)}{\text{Ga}(x|\lambda, \lambda - 1)} = \frac{x^{\alpha-1} \lambda^\alpha \exp(-\lambda x) / \Gamma(\alpha)}{x^{k-1} (\lambda - 1)^k \exp(-(\lambda - 1)x) / \Gamma(k)} = \frac{\Gamma(k) \lambda^\alpha}{\Gamma(\alpha) (\lambda - 1)^k} x^{\alpha - k} \exp(-x) \quad (11.26) (11.27)\)

当 \(x = \alpha - k$ 时，该比率达到最大值。因此

\(C = \frac{\text{Ga}(\alpha - k | \alpha, \lambda)}{\text{Ga}(\alpha - k | k, \lambda - 1)} \quad (11.28)\)

图示请参见图 11.4(b)。

3. 本节基于 Ioana A. Cosma 的笔记，可于 http://users.aims.ac.za/~ioana/cp2.pdf 查阅。

### 11.4.3 自适应拒绝采样

我们现在描述一种方法，它可以自动为任何对数凹的 1d 密度 \(p(x)$ 找到一个紧密的上包络 \(q(x)$。其思路是用分段线性函数对对数密度进行上界，如图 11.5(a) 所示。我们根据分布支撑集上的固定网格选择各段的初始位置，然后在这些位置计算对数密度的梯度，并使直线在这些点处相切。

由于包络的对数是分段线性的，包络本身是分段指数的：

\(q(x) = C_i \lambda_i \exp(-\lambda_i (x - x_{i-1})), \quad x_{i-1} < x \le x_i \quad (11.29)\)

其中 \(x_i$ 是网格点。从该分布中采样相对简单。如果样本 \(x$ 被拒绝，我们就在 \(x$ 处创建一个新网格点，从而细化包络。随着网格点数量的增加，包络的紧密性提高，拒绝率下降。这被称为 **自适应拒绝采样** (ARS) [GW92]。图 11.5(b-c) 给出了该方法的实际应用示例。与标准拒绝采样一样，它可应用于未归一化的分布。

![](img/ca72c1626f4850f058a9edc138c1ac73_515_0.png)

图 11.5：(a) 自适应拒绝采样的原理。我们在对数凹密度上放置分段线性上界（和下界）。改编自 [GW92] 的图 1。由 ars_envelope.ipynb 生成。(b-c) 使用 ARS 从半高斯分布中采样。由 ars_demo.ipynb 生成。

### 11.4.4 高维中的拒绝采样

显然，我们希望建议分布 q(x) 尽可能接近目标分布 p(x)，同时仍然是一个上界。但这很难实现，尤其是在高维中。为了理解这一点，考虑从 p(x) = N(0, sigma_p^2 I) 中采样，使用 q(x) = N(0, sigma_q^2 I) 作为建议分布。显然，为了成为上界，我们必须有 sigma_q^2 >= sigma_p^2。在 D 维中，最优值由 C = (sigma_q / sigma_p)^D 给出。接受率为 1/C（因为 p 和 q 都是归一化的），它随维度呈指数级下降。例如，如果 sigma_q 比 sigma_p 仅多 1%，那么在 1000 维中，接受率约为 1/20,000。这是拒绝采样的一个根本性弱点。

## 11.5 重要采样

在本节中，我们描述了一种称为 **重要采样** 的蒙特卡洛方法，用于近似如下形式的积分

$$\mathbb{E}[\varphi(\boldsymbol{x})] = \int \varphi(\boldsymbol{x})\pi(\boldsymbol{x})d\boldsymbol{x}$$ (11.30)

其中 \(\varphi$ 称为 **目标函数**，\(\pi(\boldsymbol{x})$ 是 **目标分布**，通常是形式为 \(\pi(\boldsymbol{x}) = p(\boldsymbol{x}|\boldsymbol{y})$ 的条件分布。由于通常很难从目标分布中抽样，我们将改为从某个 **建议分布** \(q(\boldsymbol{x})$（通常取决于 \(\boldsymbol{y}$）中抽样。然后通过为每个样本关联权重来调整这种不准确性，从而得到一个加权的 MC 近似：

$$\mathbb{E}[\varphi(\boldsymbol{x})] \approx \sum_{n=1}^N W_n \varphi(\boldsymbol{x}_n)$$ (11.31)

我们将讨论两种情况：首先是目标分布归一化的情况，然后是未归一化的情况。这将影响权重的计算方式以及估计器的统计特性。

