
作为输入，而无需任何特殊的重参数化来使噪声与模型独立。

### 20.9.1 通过离散随机操作反向传播

当模型输出一个离散变量 $\mathbf{y}$ 时，重参数化技巧不可应用。假设模型接收输入 $\mathbf{x}$ 和参数 $\boldsymbol{\theta}$，两者都封装在向量 $\boldsymbol{\omega}$ 中，并将它们与随机噪声 $\mathbf{z}$ 结合以产生 $\mathbf{y}$：

$$
\mathbf{y}=f(\mathbf{z};\boldsymbol{\omega}). \tag{20.58}
$$

因为 $\mathbf{y}$ 是离散的，所以 $f$ 必须是一个阶跃函数。阶跃函数的导数在任何点上都无用。就在每个阶跃边界处，导数未定义，但这是一个小问题。更大的问题是，导数在阶跃边界之间的区域几乎处处为零。因此，任何代价函数 $J(\mathbf{y})$ 的导数都不会提供如何更新模型参数 $\boldsymbol{\theta}$ 的信息。

REINFORCE 算法（REward Increment = nonnegative Factor × Offset Reinforcement × Characteristic Eligibility）提供了一个定义简单但强大的解族的框架（Williams, 1992）。核心思想是，尽管 $J(f(\mathbf{z};\boldsymbol{\omega}))$ 是一个具有无用导数的阶跃函数，但期望代价 $\mathbb{E}_{\mathbf{z}\sim p(\mathbf{z})}J(f(\mathbf{z};\boldsymbol{\omega}))$ 通常是一个适合梯度下降的光滑函数。尽管当 $\mathbf{y}$ 是高维的（或是由许多离散随机决策的组合产生）时，该期望通常是不可处理的，但它可以使用蒙特卡洛平均无偏地估计。梯度的随机估计可以与 SGD 或其他基于随机梯度的优化技术一起使用。

REINFORCE 的最简单版本可以通过简单地对期望代价求微分来推导：

$$
\begin{aligned}
\mathbb{E}_{\mathbf{z}}[J(\mathbf{y})] &= \sum_{\mathbf{y}} J(\mathbf{y})p(\mathbf{y}), \tag{20.59}\\
\frac{\partial \mathbb{E}[J(\mathbf{y})]}{\partial \boldsymbol{\omega}} &= \sum_{\mathbf{y}} J(\mathbf{y})\frac{\partial p(\mathbf{y})}{\partial \boldsymbol{\omega}} \tag{20.60}\\
&= \sum_{\mathbf{y}} J(\mathbf{y})p(\mathbf{y})\frac{\partial \log p(\mathbf{y})}{\partial \boldsymbol{\omega}} \tag{20.61}\\
&\approx \frac{1}{m}\sum_{i=1}^{m}J(\mathbf{y}^{(i)})\frac{\partial \log p(\mathbf{y}^{(i)})}{\partial \boldsymbol{\omega}},\quad \mathbf{y}^{(i)}\sim p(\mathbf{y}) \tag{20.62}
\end{aligned}
$$

公式 20.60 依赖于 $J$ 不直接引用 $\omega$ 的假设。扩展该方法以放宽此假设是微不足道的。公式 20.61 利用了对数求导法则，$\frac{\partial \log p(\boldsymbol{y})}{\partial \boldsymbol{\omega}} = \frac{1}{p(\boldsymbol{y})} \frac{\partial p(\boldsymbol{y})}{\partial \boldsymbol{\omega}}$。公式 20.62 给出了梯度的无偏蒙特卡洛估计器。

在本节中，我们写 $p(\boldsymbol{y})$ 的任何地方，都可以同样写成 $p(\boldsymbol{y} \mid \boldsymbol{x})$。这是因为 $p(\boldsymbol{y})$ 由 $\boldsymbol{\omega}$ 参数化，而 $\boldsymbol{\omega}$ 包含 $\boldsymbol{\theta}$ 和 $\boldsymbol{x}$，如果 $\boldsymbol{x}$ 存在。

简单 REINFORCE 估计器的问题之一是其方差非常高，因此需要抽取 $\boldsymbol{y}$ 的许多样本才能获得梯度的良好估计器，或者等价地，如果只抽取一个样本，SGD 将收敛非常缓慢并且需要更小的学习率。通过使用方差缩减方法（Wilson, 1984; L'Ecuyer, 1994）可以显著降低该估计器的方差。思路是修改估计器，使其期望值保持不变但方差减小。在 REINFORCE 的上下文中，所提出的方差缩减方法涉及计算一个用于抵消 $J(\boldsymbol{y})$ 的基线。请注意，任何不依赖于 $\boldsymbol{y}$ 的偏移 $b(\boldsymbol{\omega})$ 都不会改变估计梯度的期望，因为

$$
\begin{aligned}
E_{p(\boldsymbol{y})}\left[\frac{\partial \log p(\boldsymbol{y})}{\partial \boldsymbol{\omega}}\right]
&= \sum_{\boldsymbol{y}} p(\boldsymbol{y}) \frac{\partial \log p(\boldsymbol{y})}{\partial \boldsymbol{\omega}} \\
&= \sum_{\boldsymbol{y}} \frac{\partial p(\boldsymbol{y})}{\partial \boldsymbol{\omega}} \\
&= \frac{\partial}{\partial \boldsymbol{\omega}} \sum_{\boldsymbol{y}} p(\boldsymbol{y}) = \frac{\partial}{\partial \boldsymbol{\omega}} 1 = 0,
\end{aligned}
$$

这意味着

$$
\begin{aligned}
E_{p(\boldsymbol{y})}\left[(J(\boldsymbol{y}) - b(\boldsymbol{\omega}))\frac{\partial \log p(\boldsymbol{y})}{\partial \boldsymbol{\omega}}\right]
&= E_{p(\boldsymbol{y})}\left[J(\boldsymbol{y})\frac{\partial \log p(\boldsymbol{y})}{\partial \boldsymbol{\omega}}\right] - b(\boldsymbol{\omega})E_{p(\boldsymbol{y})}\left[\frac{\partial \log p(\boldsymbol{y})}{\partial \boldsymbol{\omega}}\right] \\
&= E_{p(\boldsymbol{y})}\left[J(\boldsymbol{y})\frac{\partial \log p(\boldsymbol{y})}{\partial \boldsymbol{\omega}}\right].
\end{aligned}
$$

此外，我们可以通过计算 $(J(\boldsymbol{y}) - b(\boldsymbol{\omega}))\frac{\partial \log p(\boldsymbol{y})}{\partial \boldsymbol{\omega}}$ 在 $p(\boldsymbol{y})$ 下的方差并关于 $b(\boldsymbol{\omega})$ 最小化来获得最优的 $b(\boldsymbol{\omega})$。我们发现，这个最优基线 $b^{*}(\boldsymbol{\omega})_{i}$ 对向量 $\boldsymbol{\omega}$ 的每个元素 $\omega_{i}$ 都是不同的：

$$
b^{*}(\boldsymbol{\omega})_{i} = \frac{E_{p(\boldsymbol{y})}\left[J(\boldsymbol{y})\left(\frac{\partial \log p(\boldsymbol{y})}{\partial \omega_{i}}\right)^{2}\right]}{E_{p(\boldsymbol{y})}\left[\left(\frac{\partial \log p(\boldsymbol{y})}{\partial \omega_{i}}\right)^{2}\right]}. \tag{20.68}
$$

关于 $\omega_i$ 的梯度估计器随后变为

$$
(J(\boldsymbol{y}) - b(\boldsymbol{\omega})_i)\frac{\partial \log p(\boldsymbol{y})}{\partial \omega_i}, \tag{20.69}
$$

其中 $b(\boldsymbol{\omega})_i$ 估计上述 $b^*(\boldsymbol{\omega})_i$。估计值 $b$ 通常通过向神经网络添加额外输出并训练新输出来估计 $E_{p(\boldsymbol{y})}\left[J(\boldsymbol{y})\left(\frac{\partial \log p(\boldsymbol{y})}{\partial \omega_i}\right)^2\right]$ 和 $E_{p(\boldsymbol{y})}\left[\left(\frac{\partial \log p(\boldsymbol{y})}{\partial \omega_i}\right)^2\right]$ 对于 $\boldsymbol{\omega}$ 的每个元素而获得。这些额外输出可以用均方误差目标进行训练，分别使用 $J(\boldsymbol{y})\left(\frac{\partial \log p(\boldsymbol{y})}{\partial \omega_i}\right)^2$ 和 $\left(\frac{\partial \log p(\boldsymbol{y})}{\partial \omega_i}\right)^2$ 作为目标，当 $\boldsymbol{y}$ 从 $p(\boldsymbol{y})$ 中采样时，对给定的 $\boldsymbol{\omega}$。然后可以通过将这些估计值代入公式 20.68 来恢复估计值 $b$。Mnih 和 Gregor (2014) 倾向于使用单个共享输出（跨 $\boldsymbol{\omega}$ 的所有元素 $i$）并以 $J(\boldsymbol{y})$ 为目标进行训练，使用基线 $b(\boldsymbol{\omega}) \approx E_{p(\boldsymbol{y})}[J(\boldsymbol{y})]$。

方差缩减方法已在强化学习背景下引入（Sutton et al., 2000; Weaver and Tao, 2001），推广了 Dayan (1990) 关于二元奖励情况的先前工作。参见 Bengio et al. (2013b)、Mnih and Gregor (2014)、Ba et al. (2014)、Mnih et al. (2014) 或 Xu et al. (2015)，以了解在深度学习背景下使用方差缩减的 REINFORCE 算法的现代用例的例子。除了使用输入相关的基线 $b(\boldsymbol{\omega})$ 之外，Mnih 和 Gregor (2014) 发现 $(J(\boldsymbol{y}) - b(\boldsymbol{\omega}))$ 的尺度可以在训练期间通过将其除以在训练期间通过移动平均估计的标准差来调整，作为一种自适应学习率，以抵消在训练过程中该数量大小发生的重要变化的影响。Mnih 和 Gregor (2014) 将此启发式方法称为 **方差归一化**。

基于 REINFORCE 的估计器可以被理解为通过将 $\boldsymbol{y}$ 的选择与相应的 $J(\boldsymbol{y})$ 值相关联来估计梯度。如果在当前参数化下，$\boldsymbol{y}$ 的一个好的值不太可能出现，可能需要很长时间才能偶然获得它并得到该配置应被强化的所需信号。

## 20.10 有向生成网络

如第 16 章所述，有向图模型构成了图模型的一个重要类别。虽然有向图模型在更广泛的机器学习社区中非常受欢迎，但在较小的深度学习社区中，直到大约 2013 年，它们一直被 RBM 等无向模型所 overshadow。
