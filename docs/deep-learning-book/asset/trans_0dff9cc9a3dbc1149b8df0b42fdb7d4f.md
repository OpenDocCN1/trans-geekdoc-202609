
## 算法 8.1 随机梯度下降 (SGD) 更新

```
**Require:** Learning rate schedule ε₁, ε₂, …
**Require:** Initial parameter **θ**
  k ← 1
  **while** stopping criterion not met **do**
    Sample a minibatch of m examples from the training set {**x**^(1), …, **x**^(m)} with corresponding targets **y**^(i).
    Compute gradient estimate: **ĝ** ← (1/m)∇_θ Σ_i L(f(**x**^(i); θ), **y**^(i))
    Apply update: **θ** ← **θ** − ε_k **ĝ**
    k ← k + 1
  **end while**
```

下降，因此批量梯度下降可以使用固定的学习率。保证 SGD 收敛的一个充分条件是

∑_{k=1}^{∞} ε_k = ∞,  and  (8.12)

∑_{k=1}^{∞} ε_k^2 < ∞.  (8.13)

在实践中，通常在迭代 τ 之前线性衰减学习率：

ε_k = (1 − α) ε_0 + α ε_τ  (8.14)

其中 α = k/τ。迭代 τ 之后，通常保持 ε 不变。

学习率可以通过试错来选择，但通常最好通过监控随时间变化的目标函数值的学习曲线来选择。这更多是一种艺术而非科学，对此主题的大多数指导都应持一定怀疑态度。使用线性调度时，需要选择的参数为 ε_0、ε_τ 和 τ。通常 τ 可以设为完成训练集几次百次遍历所需的迭代次数。通常 ε_τ 应设为 ε_0 大约 1% 的值。主要问题是如何设置 ε_0。如果它太大，学习曲线将显示剧烈振荡，代价函数经常显著增加。轻微振荡是可以的，尤其是在使用随机代价函数训练时，例如使用 dropout 产生的代价函数。如果学习率太低，学习进展缓慢，如果初始学习率太低，学习可能会卡在较高的代价值。 通常，就总训练时间和

最终代价值而言，最优初始学习率高于在最初 100 次迭代左右获得最佳性能的学习率。因此，通常最好监控最初几次迭代，并使用高于此时最佳性能的学习率，但又不能高到导致严重不稳定。

SGD 以及相关的基于 minibatch 或在线梯度优化的最重要特性是每次更新的计算时间不会随训练示例数量增长。这使得即使训练示例数量变得非常大时也能收敛。对于足够大的数据集，SGD 可能在处理完整个训练集之前就收敛到其最终测试集误差的某个固定容差范围内。

为了研究优化算法的收敛速度，通常测量 **超额误差** $J(\theta) - \min_{\theta} J(\theta)$，即当前代价函数超过最小可能代价的量。当 SGD 应用于凸问题时，$k$ 次迭代后的超额误差为 $O(1/\sqrt{k})$，而在强凸情况下，为 $O(1/k)$。除非假设额外条件，否则这些界限无法改进。批量梯度下降在理论上比随机梯度下降具有更好的收敛速度。然而，Cramér–Rao 界限 (Cramér, 1946; Rao, 1945) 指出，泛化误差不可能比 $O(1/k)$ 更快地减小。Bottou 和 Bousquet (2008) 认为，因此对于机器学习任务，追求收敛速度快于 $O(1/k)$ 的优化算法可能不值得——更快的收敛很可能对应于过拟合。此外，渐近分析掩盖了随机梯度下降在少量步数后所具有的许多优势。对于大型数据集，SGD 在评估很少的示例梯度时就能快速取得初始进展的能力，超过了其缓慢的渐近收敛。本章其余部分描述的大多数算法实现了在实践中重要的收益，但在 $O(1/k)$ 渐近分析所掩盖的常数因子中丢失了这些收益。还可以通过在学习过程中逐渐增大 minibatch 大小来权衡批量和随机梯度下降的优点。

有关 SGD 的更多信息，请参阅 Bottou (1998)。

## 8.3.2 动量

虽然随机梯度下降仍然是一种流行的优化策略，但使用它进行学习有时会很慢。动量法 (Polyak, 1964) 的设计目的是加速学习，尤其是在曲率较高、梯度小但一致或梯度噪声较大时。动量算法累积过去梯度的指数衰减移动平均并继续沿其方向移动

![](img/e7937519e1e39a29aca97c7de303ca30_309_0.png)

图 8.5：动量主要旨在解决两个问题：Hessian 矩阵的病态条件和随机梯度的方差。这里，我们说明动量如何克服这两个问题中的第一个。等高线描绘了一个具有病态 Hessian 矩阵的二次损失函数。穿过等高线的红色路径表示动量学习规则在最小化该函数时遵循的路径。在每一步中，我们画出一个箭头，表示该点梯度下降会采取的步长。我们可以看到，病态的二次目标看起来像一个长而窄的山谷或峡谷，两侧陡峭。动量正确地沿峡谷长度方向遍历，而梯度步浪费时间在峡谷狭窄轴线上来回移动。另请比较图 4.6，其中显示了没有动量的梯度下降的行为。

沿其方向。动量的效果如图 8.5 所示。

形式上，动量算法引入一个变量 v 起速度的作用——它是参数在参数空间中移动的方向和速度。速度被设为负梯度的指数衰减平均值。动量的名称源于物理类比，其中负梯度是根据牛顿运动定律在参数空间中移动粒子的力。物理中的动量是质量乘以速度。在动量学习算法中，我们假设单位质量，因此速度向量 v 也可视为粒子的动量。超参数 α ∈ [0, 1) 决定了先前梯度贡献的指数衰减速度。更新规则为

v ← αv − ε∇θ ( 1/m Σ_{i=1}^m L(f(x^(i); θ), y^(i)) ),    (8.15)
θ ← θ + v.    (8.16)

## 算法 8.2 带动量的随机梯度下降 (SGD)

```
Require: Learning rate $\epsilon$, momentum parameter $\alpha$
Require: Initial parameter $\boldsymbol{\theta}$, initial velocity $\boldsymbol{v}$

while stopping criterion not met do
    Sample a minibatch of $m$ examples from the training set $\{\boldsymbol{x}^{(1)}, \ldots, \boldsymbol{x}^{(m)}\}$ with corresponding targets $\boldsymbol{y}^{(i)}$.
    Compute gradient estimate: $\boldsymbol{g} \leftarrow \frac{1}{m}\nabla_{\boldsymbol{\theta}}\sum_i L(f(\boldsymbol{x}^{(i)}; \boldsymbol{\theta}), \boldsymbol{y}^{(i)})$.
    Compute velocity update: $\boldsymbol{v} \leftarrow \alpha\boldsymbol{v} - \epsilon\boldsymbol{g}$.
    Apply update: $\boldsymbol{\theta} \leftarrow \boldsymbol{\theta} + \boldsymbol{v}$.
end while
```

速度 $\boldsymbol{v}$ 累积梯度元素 $\nabla_{\boldsymbol{\theta}}\left(\frac{1}{m}\sum_{i=1}^{m} L(f(\boldsymbol{x}^{(i)}; \boldsymbol{\theta}), \boldsymbol{y}^{(i)})\right)$。$\alpha$ 相对于 $\epsilon$ 越大，先前的梯度对当前方向的影响越大。带动量的 SGD 算法如算法 8.2 所示。

以前，步长的大小只是梯度范数乘以学习率。现在，步长的大小取决于一系列梯度有多大以及它们是否一致。当许多连续梯度完全指向同一方向时，步长最大。如果动量算法始终观察到梯度 $\boldsymbol{g}$，那么它将沿 $-\boldsymbol{g}$ 的方向加速，直到达到终端速度，此时每次步长的大小为

$$\frac{\epsilon\|\boldsymbol{g}\|}{1-\alpha}. \tag{8.17}$$

因此，以 $\frac{1}{1-\alpha}$ 的形式思考动量超参数是有帮助的。例如，$\alpha=0.9$ 相对于梯度下降算法将最大速度乘以 10。

实践中常用的 $\alpha$ 值包括 0.5、0.9 和 0.99。与学习率一样，$\alpha$ 也可随时间自适应。通常它从一个较小的值开始，然后提高。随着时间的推移自适应 $\alpha$ 的重要性不如随着时间的推移缩小 $\epsilon$。

我们可以将动量算法视为模拟受连续时间牛顿动力学支配的粒子。物理类比有助于建立对动量和梯度下降算法行为的直觉。

粒子在任意时刻的位置由 $\boldsymbol{\theta}(t)$ 给出。粒子受到净力 $\boldsymbol{f}(t)$ 的作用。该力导致粒子加速：

$$\boldsymbol{f}(t)=\frac{\partial^2}{\partial t^2}\boldsymbol{\theta}(t). \tag{8.18}$$

