

![](img/1feac31c3be82ff11343dd49645de758_69_0.png)

![](img/1feac31c3be82ff11343dd49645de758_69_1.png)

图7.3. 使用MLP的泊松方程。（a）归一化谱的直方图（特征值乘以学习率）。（b）损失与轮数的关系。图取自De Ryck等人（2023）。

先前考虑的预处理傅里叶特征模型的局部化谱，与其快速训练也相关（图7.1(b)）。

然而，对于神经网络等非线性模型，预处理A通常可能很困难。这里我们考虑一种简单的策略，将MLP与上述定义的傅里叶特征φ_k耦合，即设置

$u_\theta = \Phi_\theta\left(\sum_k \alpha_k \phi_k\right)$。

直观地说，我们必须仔细选择α_k来控制 (d^{2n}/dx^{2n}) u_θ(x)，因为它将包含以下各项

$\left(\sum_{k\neq0} \alpha_k (-k)^{2n} \phi_k\right) \Phi_\theta^{(2n)}\left(\sum_k \alpha_k \phi_k\right)$。

因此，这种重新缩放可以更好地调节微分算子的Hermitian平方。为了在泊松方程中测试这一点，我们在该FF-MLP模型中选择α_k = 1/k^2（对于k ≠ 0），并将特征值呈现在图7.3(a)中，这表明尽管仍有一些（接近）零特征值，但非零特征值的数量显著增加，与未预处理的MLP情况相比，谱的分布更加均匀。这可能是损失函数衰减得更快的原因，如图7.3(b)所示，与未预处理的MLP相比。

## 7.5. 改进物理信息机器学习训练的策略

鉴于训练物理信息机器学习模型遇到的困难，近期文献中提出了几种特设策略来改进训练。事实证明，其中许多策略也可以用预处理来解释。

### 7.5.1. *$\lambda$ 的选择*

物理信息损失（如(2.46)）中的参数$\lambda$起着关键作用，因为它平衡了物理信息损失$R$与边界监督损失$B$的相对贡献。根据前几节的分析，自然建议该参数应选择为

$$\lambda^* := \underset{\lambda}{\min}\; \kappa(\mathbf{A}(\lambda)) \tag{7.33}$$

以获得$\mathbf{A}$的最小条件数并加速收敛。另一个策略由Wang等人 (2021a) 提出，他们建议使用学习率退火算法在训练过程中迭代更新$\lambda$，如下所示：

$$\lambda_a^* := \frac{\max_k\left|(\nabla_\theta R(\theta))_k\right|}{(2K+1)^{-1}\sum_k\left|(\nabla_\theta B(\theta))_k\right|}. \tag{7.34}$$

类似地，Wang等人 (2022b) 提出设置

$$\lambda_b^* := \frac{\operatorname{Tr}(K_{rr}(n))}{\operatorname{Tr}(K_{uu}(n))} \approx \frac{\int_\Omega \nabla_\theta\mathcal{L}u_\theta^\top\nabla_\theta\mathcal{L}u_\theta}{\int_{\partial\Omega}\nabla_\theta u_\theta^\top\nabla_\theta u_\theta}. \tag{7.35}$$

关于$K_{rr}$和$K_{uu}$的精确定义，我们参考Wang等人 (2022b)。

在下面的示例中，我们针对泊松方程比较了$\lambda^*$ (7.33)、$\lambda_a^*$ (7.34) 和$\lambda_b^*$ (7.35)。

**示例7.13（泊松方程）。** 我们针对一维泊松方程和使用频率至$K$的傅里叶特征的线性模型，比较上述三种策略。首先，De Ryck等人 (2023) 计算出$\lambda^* \sim K^2$。接下来，为了计算$\lambda_a^*$，我们观察到对于$k\ne \ell$，$(\nabla_\theta R(\theta))_k = k^4\theta_k$，且$(\nabla_\theta R(\theta))_\ell = \ell^4(\theta_\ell-1)$。我们发现初始化时$\max_k |(\nabla_\theta R(\theta))_k| \sim K^4$。接下来我们计算（给定初始化时$\theta_m\sim\mathcal{N}(0,1)$独立同分布）

$$\mathbb{E}\sum_k\left|(\nabla_\theta B(\theta))_k\right| = \sum_{k=0}^{K}\mathbb{E}\left|\sum_{m=0}^{K}\theta_m(-1)^{k+m}\right| = \sum_{k=0}^{K}\mathbb{E}\left|\sum_{m=0}^{K}\theta_m\right| = (K+1)^{3/2}. \tag{7.36}$$

由此我们得到粗略估计

$$(2K+1)^{-1}\sum_k\left|(\nabla_\theta B(\theta))_k\right|\sim\sqrt{K}.$$

因此总体上我们发现$\lambda_a^*\sim K^{3.5}$。最后，对于$\lambda_b^*$，可以做出估计

$$\lambda_b^*\approx \frac{2\pi\sum_{k=1}^{K}k^4}{K+1}\sim K^4. \tag{7.37}$$

因此，结果表明，对于傅里叶特征模型，应用这些不同策略会导致$\lambda$随$K$增加而具有不同的缩放比例。尽管存在这些差异，但观察到所得条件数$\kappa(\mathbf{A}(\lambda^*))$、$\kappa(\mathbf{A}(\lambda_a^*))$和$\kappa(\mathbf{A}(\lambda_b^*))$实际上非常相似。

### 7.5.2. 硬边界条件

从PINNs（Lagaris等人 1998, 2000）问世起，一些作者就主张修改机器学习模型，使得PDE (2.1)中的边界条件被精确施加，且(2.46)中的边界损失为零。这种硬施加边界条件（BC）已被经验证明有助于训练；例如见Dong和Ni (2021)、Moseley等人 (2023)、Dolean等人 (2023) 及其参考文献。这可以通过以下方式解释：实现硬边界条件通过改变算子TT*，导致不同的矩阵A。

我们首先考虑一个玩具模型，以直接的方式展示这些现象。我们再次考虑具有零Dirichlet边界条件的泊松方程−Δu = − sin（见示例2.4）。我们选择模型

$$u_{\theta}(x) = \theta_{-1} \cos(x) + \theta_{0} + \theta_{1} \sin(x), \tag{7.38}$$

并报告De Ryck等人 (2023) 中各种软边界条件和硬边界条件变体之间的条件数比较。

- *软边界条件。* 如果我们使用(7.33)设置最优λ，我们发现最优λ*的条件数为3 + 2√2 ≈ 5.83。
- *硬边界条件：变体1。* 实现硬边界条件的第一种常用方法是将模型乘以一个函数η(x)，使得乘积精确满足边界条件，而不论uθ如何。在我们的设置中，我们可以考虑η(x)uθ(x)且η(±π) = 0。对于η = sin，总模型为

$$\eta(x)u_{\theta}(x) = -\frac{\theta_{-1}}{2}\cos(2x) + \frac{\theta_{-1}}{2} + \theta_{0} \sin(x) + \frac{\theta_{1}}{2} \sin(2x), \tag{7.39}$$

并产生条件数4。选择不同的η将不可避免地导致不同的条件数。
- *硬边界条件：变体2。* 另一个选择是从模型中减去uθ(π)，以便精确满足边界条件。这对应于模型

$$u_{\theta}(x) - u_{\theta}(\pi) = \theta_{-1}(\cos(x) + 1) + \theta_{1} \sin(x). \tag{7.40}$$

注意，这意味着可以丢弃θ0作为参数，仅留下两个可训练参数。相应的条件数为1。

因此，在本例中，硬边界条件的条件数严格小于软边界条件的条件数，即

$$\kappa(\mathbb{A}_{\text{hard BC}}) < \min_{\lambda} \kappa(\mathbb{A}_{\text{soft BC}}(\lambda)). \tag{7.41}$$

这种现象也可以在其他PDE中观察到，例如线性平流方程（De Ryck等人 2023）。

### 7.5.3. 二阶优化器

大量实证研究表明，（随机）梯度下降或ADAM等一阶优化器不适用于物理信息机器学习，我们需要使用L-BFGS等二阶（拟）Newton型优化器，才能使物理信息机器学习模型的训练可行。事实证明，对于线性物理信息模型，损失函数的Hessian矩阵与矩阵$\mathbb{A}$ (7.13)相同。给定任何损失$\mathcal{J}(\theta)$，Newton方法的梯度流为

$$\frac{\mathrm{d}\theta(t)}{\mathrm{d}t} = -\gamma H[\mathcal{J}(\theta(t))]^{-1}\nabla_{\theta}\mathcal{J}(\theta(t)),\qquad (7.42)$$

其中$H$是Hessian矩阵。在我们的情况下，我们考虑物理信息损失$L(\theta) = R(\theta) + \lambda B(\theta)$，并考虑模型$u_\theta(x) = \sum_{\ell} \theta_\ell \phi_\ell(x)$，这对应于线性模型或NTK机制下的神经网络（例如引理7.8）。利用$\partial_{\theta_i}\partial_{\theta_j} u_\theta = 0$，我们计算

$$\begin{aligned}
\partial_{\theta_i}\partial_{\theta_j} L(\theta) &= \int_{\Omega} (\mathcal{L}\partial_{\theta_i} u_\theta(x)) \cdot \mathcal{L}\partial_{\theta_j} u_\theta(x)\,\mathrm{d}x + \lambda \int_{\partial\Omega} \partial_{\theta_i} u_{\theta}(x) \cdot \partial_{\theta_j} u_\theta(x)\,\mathrm{d}x \\
&= \int_{\Omega} \mathcal{L}\phi_i(x) \cdot \mathcal{L}\phi_j(x)\,\mathrm{d}x + \lambda \int_{\partial\Omega} \phi_i(x) \cdot \phi_j(x)\,\mathrm{d}x \\
&= \mathbb{A}_{i j}.
\end{aligned}\qquad (7.43)$$

因此，在这种情况下，（拟）Newton方法自动计算Hessian的（近似）逆，从而预处理矩阵$\mathbb{A}$，将（拟）Newton型优化器的使用与此处的预处理算子联系起来。有关此联系的进一步分析，参见Müller和Zeinhofer (2023)。

### 7.5.4. 区域分解

区域分解（DD）是数值分析中广泛使用的技术，用于预处理由经典方法（如有限元）产生的线性系统（Dolean, Jolivet和Nataf 2015）。最近，有研究尝试将DD启发的算法用于物理信息机器学习（见Moseley等人 2023，Dolean等人 2023 及其参考文献），尽管尚未建立与模型预处理的显式联系。De Ryck等人 (2023) 在线性平流方程中建立了这种联系，他们计算出$\mathbb{A}$的条件数二次依赖于平流速度$\beta$。他们认为，在$[0, T]$的子区间上考虑$N$个相同的子模型，本质上等同于重新缩放$\beta$。由于条件数按$\beta^2$缩放，将时间域分成$N$部分将使每个子模型的条件数减少$N^2$倍。这也与基于因果学习的PINN训练（Wang, Sankaran和Perdikaris 2024）内在相关，因此也可以视为改善条件数的一种策略。

