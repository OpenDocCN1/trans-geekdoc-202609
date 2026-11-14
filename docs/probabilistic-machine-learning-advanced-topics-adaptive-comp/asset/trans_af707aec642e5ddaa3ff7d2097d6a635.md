

由于积分号下的分布取决于微分参数 \(\boldsymbol{\theta}\)，因此我们不能改变微分与积分的顺序。相反，我们将使用 \(q_\theta(\boldsymbol{x})\) 是由隐式生成模型诱导的分布（也称为“重参数化技巧”，见第 6.3.5 节）：\(\nabla_\theta L_G(\boldsymbol{\phi}, \boldsymbol{\theta}) = \nabla_\theta \mathbb{E}_{q_\theta(\boldsymbol{x})}[l(D_\phi(\boldsymbol{x}))] = \nabla_\theta \mathbb{E}_{q(\boldsymbol{z})}[l(D_\phi(G_\theta(\boldsymbol{z})))] = \mathbb{E}_{q(\boldsymbol{z})}\nabla_\theta[l(D_\phi(G_\theta(\boldsymbol{z})))]\)，并再次使用蒙特卡罗估计，利用先验 \(q(\boldsymbol{z})\) 的样本近似梯度。将算法 26.1 中的损失函数选择和蒙特卡罗估计替换后，得到算法 26.2，该算法常用于训练 GAN。

```
Algorithm 26.2: GAN training algorithm
Initialize \(\phi, \theta\)
for each training iteration do
  for K steps do
    Sample minibatch of M noise vectors \(\boldsymbol{z}_m \sim q(\boldsymbol{z})\)
    Sample minibatch of M examples \(\boldsymbol{x}_m \sim p^*(\boldsymbol{x})\)
    Update the discriminator by performing stochastic gradient descent using this gradient:
    \(\nabla_\phi \frac{1}{M} \sum_{m=1}^M [l(D_\phi(\boldsymbol{x}_m)) + h(D_\phi(G_\theta(\boldsymbol{z}_m)))]\).
  Sample minibatch of M noise vectors \(\boldsymbol{z}_m \sim q(\boldsymbol{z})\)
  Update the generator by performing stochastic gradient descent using this gradient:
  \(\nabla_\theta \frac{1}{M} \sum_{m=1}^M l(D_\phi(G_\theta(\boldsymbol{z}_m)))\).
Return \(\phi, \theta\)
```

### 26.3.3 GAN 训练中的挑战

由于 GAN 的对抗博弈特性，GAN 的优化动力学既难以在理论上研究，也难以在实践中稳定。GAN 已知会出现 **模式崩溃** 现象，即生成器收敛到一个分布，该分布未涵盖数据分布的所有模式（峰值），因此模型对分布欠拟合。我们在图 26.6 中展示了一个例子：虽然数据是包含 16 个模式的高斯混合分布，但模型只收敛到其中的几个模式。或者，另一种问题行为是 **模式跳跃**，即生成器在生成数据分布的不同模式之间“跳跃”。对此行为的直观解释如下：如果生成器擅长从某个模式生成数据，它将从该模式生成更多数据。如果判别器无法学会在该模式中区分真实数据和生成数据，生成器就没有动力扩展其支持并生成其他模式的数据。另一方面，如果判别器最终学会区分该模式内的真实数据和生成数据，生成器可以简单地移动（跳跃）到一个新模式，这种猫鼠游戏可以继续进行。虽然模式崩溃和模式跳跃通常与 GAN 相关联，但许多改进已使 GAN 训练更加稳定，并使这些行为更加罕见。这些改进包括使用大批量大小、增加判别器神经容量、使用判别器和生成器正则化，以及更复杂的优化方法。

![](img/ca72c1626f4850f058a9edc138c1ac73_929_0.png)

图 26.6：GAN 训练中模式崩溃和模式跳跃的示意图。(a) 数据集，二维空间中 16 个高斯分布的混合。(b-f) 经过不同数量训练后的模型样本。由 gan_mixture_of_gaussians.ipynb 生成。

### 26.3.4 改进 GAN 优化

在训练 GAN 时，诸如动量选择等超参数选择可能至关重要，与监督学习中常用的高动量相比，较低的动量值更受青睐。Adam [KB14a] 等算法可大幅提升性能 [RMC16a]。许多其他优化方法已成功应用于 GAN，例如针对方差减小的方法 [Cha+19c]；通过梯度步骤反向传播的方法，从而在判别器更新后确保生成器对抗判别器表现良好 [Met+16]；或使用双人博弈的局部双线性近似 [SA19]。虽然前景看好，但这些高级优化方法往往计算成本更高，与效率较低的优化方法相比，更难扩展到大型模型或大型数据集。

### 26.3.5 GAN 训练的收敛性

GAN 优化的挑战使得量化收敛发生时间变得困难。在第 26.2 节中，我们了解到，在从不同分布差异和距离构建的多个目标的最优性条件下，可以提供全局收敛保证：如果判别器是最优的，生成器正在最小化数据与模型分布之间的分布差异或距离，因此在无限容量和完美优化下可以学习数据分布。自原始 GAN 论文 [Goo+14] 以来，这种论证一直被用于将 GAN 与生成模型中的标准目标联系起来，并获得相关的理论保证。从博弈论角度看，这种收敛保证为 GAN 博弈的全局纳什均衡提供了存在性证明，尽管是在强假设下。当两名玩家（判别器和生成器）如果决定通过更改参数来行动都会遭受损失时，就实现了纳什均衡。考虑由方程 26.19 中的目标定义的原始 GAN；则 \(q_\theta = p^*\) 且 \(D_\phi(x) = \frac{p^*(x)}{p^*(x)+q_\theta(x)} = \frac{1}{2}\) 是一个全局纳什均衡，因为对于给定的 \(q_\theta\)，比率 \(\frac{p^*(x)}{p^*(x)+q_\theta(x)}\) 是最优判别器（方程 26.11），并且给定最优判别器，数据分布是最优生成器，因为它是 Jensen-Shannon 差异（方程 26.15）的最小化器。

虽然这些全局理论保证对 GAN 博弈提供了有用的见解，但它们没有考虑到在考虑两名玩家优化轨迹或神经网络参数化时出现的优化挑战，因为它们假设判别器和生成器都具有无限容量。在实践中，GAN 在每个优化步骤中并不一定减小距离或差异 [Fed+18]，并且在使用梯度下降等优化方法时，很难获得全局保证。相反，焦点转向局部收敛保证，例如达到局部纳什均衡。局部纳什均衡要求两名玩家都位于局部而非全局最小值：局部纳什均衡是一个驻点（两个损失函数的梯度均为零，即 \(\nabla_\phi L_D(\phi, \theta) = 0\) 和 \(\nabla_\theta L_G(\phi, \theta) = 0\)），并且每个玩家的 Hessian 矩阵（\(\nabla_\phi \nabla_\phi L_D(\phi, \theta)\) 和 \(\nabla_\theta \nabla_\theta L_G(\phi, \theta)\)）的特征值均非负；关于连续博弈中纳什均衡的更长讨论，见 [RBS16]。对于一般 GAN 博弈，不能保证局部纳什均衡始终存在 [FO20]，并且已研究了诸如驻点或局部稳定驻点等较弱条件 [Ber+19]；其他受博弈论启发的均衡定义也已被使用 [JNJ20; HLC19]。

为了说明收敛分析在 GAN 情况下的重要性，我们可视化了一个使用梯度下降训练但不收敛的 GAN 示例。在 DiracGAN [MGN18a] 中，数据分布 \(p^*(x)\) 是质量在零处的 Dirac delta 分布。生成器正在建模参数为 \(\theta\) 的 Dirac delta 分布：\(G_\theta(z) = \theta\)，而判别器是输入的线性函数，带有学习参数 \(\phi\)：\(D_\phi(x) = \phi x\)。我们还假设一种 GAN 表述，其中在上面定义的一般损失函数 \(L_D\) 和 \(L_G\) 中 \(g = h = -l\)，见方程 (26.44) 和 (26.45)。这导致了以下给出的零和游戏：

```
\(L_D = \mathbb{E}_{p^*(x)} - l(D_\phi(x)) + \mathbb{E}_{q_\theta(x)} - l(D_\phi(x)) = -l(0) - l(\theta\phi)\) (26.50)
\(L_G = \mathbb{E}_{p^*(x)} l(D_\phi(x)) + \mathbb{E}_{q_\theta(x)} l(D_\phi(x)) = +l(0) + l(\theta\phi)\) (26.51)
```

其中 \(l\) 取决于所使用的 GAN 表述（例如 \(l(z) = -\log(1 + e^{-z})\)）。唯一的均衡点是 \(\theta = \phi = 0\)。我们在图 26.7 中可视化了 DiracGAN 问题，并表明使用交替梯度下降（算法 26.1）的 DiracGAN 不会达到均衡点，而是在均衡点周围采取圆形轨迹。

为了理解均衡点附近的 GAN 收敛行为，主要采用两种理论方法：分析梯度下降的离散动力学，或使用诸如稳定性分析等方法分析博弈的底层连续动力学。为了理解两种方法之间的区别，请考虑由梯度下降定义的离散动力学

