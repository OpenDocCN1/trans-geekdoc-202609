
因此，对于局部二次函数（具有正定**H**），通过用**H**⁻¹对梯度进行缩放，牛顿法直接跳到最小值。如果目标函数是凸的但不是二次的（存在高阶项），则可以迭代此更新，从而产生与牛顿法相关的训练算法，如算法**8.8**所示。

对于非二次曲面，只要Hessian保持正定，就可以迭代应用牛顿法。这意味着一个两步迭代过程。首先，更新或计算逆Hessian（即通过更新二次近似）。其次，根据方程**8.27**更新参数。

在**8.2.3**节中，我们讨论了牛顿法仅在Hessian正定时才适用。在深度学习中，目标函数的曲面通常是非凸的，具有许多特征，例如鞍点，这些特征对牛顿法来说是有问题的。如果Hessian的特征值不全是正数，例如在鞍点附近，牛顿法实际上可能导致更新向错误方向移动。这种情况可以通过正则化Hessian来避免。常见的正则化策略包括在Hessian的对角线上添加一个常数α。正则化更新变为

θ* = θ₀ − [H(θ₀) + αI]⁻¹∇θf(θ₀).  (8.28)

这种正则化策略用于牛顿法的近似方法中，例如Levenberg-Marquardt算法（Levenberg, 1944; Marquardt, 1963），并且只要Hessian的负特征值仍然相对接近零，它就表现得相当好。当存在更极端的曲率方向时，α的值必须足够大以抵消负特征值。然而，随着α增大，Hessian将被αI对角项主导，

```
Algorithm 8.8  Newton’s method with objective J(θ) = (1/m) Σᵢ₌₁ᵐ L(f(x⁽ⁱ⁾; θ), y⁽ⁱ⁾)

Require:  Initial parameter θ₀
Require:  Training set of m examples

while stopping criterion not met do
    Compute gradient:  g ← (1/m) ∇θ Σᵢ L(f(x⁽ⁱ⁾; θ), y⁽ⁱ⁾)
    Compute Hessian:    H ← (1/m) ∇²θ Σᵢ L(f(x⁽ⁱ⁾; θ), y⁽ⁱ⁾)
    Compute Hessian inverse:  H⁻¹
    Compute update:  Δθ = −H⁻¹g
    Apply update:  θ = θ + Δθ
end while
```

并且牛顿法选择的方向收敛于标准梯度除以α。当存在强负曲率时，α可能需要大到使牛顿法比使用适当学习率的梯度下降迈出的步长还要小。

除了目标函数的某些特征（如鞍点）带来的挑战之外，牛顿法在训练大型神经网络中的应用还受到其带来的巨大计算负担的限制。Hessian中元素的数量是参数数量的平方，因此对于k个参数（即使对于非常小的神经网络，参数数量k也可能达到数百万），牛顿法需要求一个k × k矩阵的逆，其计算复杂度为O(k³)。此外，由于参数每次更新都会变化，因此必须在每次训练迭代时计算逆Hessian。因此，实际上只有参数数量非常少的网络才能通过牛顿法进行训练。在本节的其余部分，我们将讨论一些替代方法，这些方法试图在规避计算障碍的同时获得牛顿法的一些优势。

## 8.6.2 共轭梯度

共轭梯度是一种通过迭代地沿**共轭方向**下降来有效避免计算逆Hessian的方法。这种方法的灵感来源于对最速下降法（详见第4.3节）弱点的仔细研究，其中最速下降法沿与梯度相关的方向迭代地执行线搜索。图8.6说明了最速下降法在二次碗形曲面上的进展如何呈现出相当低效的来回之字形模式。这是因为每次由梯度给出的线搜索方向都保证与先前的线搜索方向正交。

设先前的搜索方向为d_{t−1}。在线搜索终止的最小值处，方向d_{t−1}上的方向导数为零：∇_θ J(θ) · d_{t−1} = 0。由于该点的梯度定义了当前搜索方向，d_t = ∇_θ J(θ) 在d_{t−1}方向上没有分量。因此d_t与d_{t−1}正交。图8.6通过多次最速下降迭代说明了d_{t−1}和d_t之间的这种关系。如图所示，选择正交的下降方向并不能保持先前搜索方向上的最小值。这导致了之字形的进展模式，即通过沿当前梯度方向下降到最小值，我们必须重新最小化先前梯度方向上的目标函数。因此，每次线搜索结束时沿梯度方向前进，在某种意义上，我们正在撤消已经

![](img/e7937519e1e39a29aca97c7de303ca30_326_0.png)

图8.6：最速下降法应用于二次代价曲面。最速下降法在每一步都沿着初始点梯度定义的直线跳到代价最低的点。这解决了图4.6中使用的固定学习率所看到的一些问题，但即使采用最优步长，算法仍然会来回地朝着最优点前进。根据定义，在目标沿给定方向的最小值处，终点的梯度与该方向正交。

在先前线搜索方向上取得的进展。共轭梯度方法旨在解决这个问题。

在共轭梯度方法中，我们寻求找到与先前线搜索方向共轭的搜索方向；也就是说，它不会撤消在该方向上取得的进展。在训练迭代t时，下一个搜索方向d_t的形式为：

d_t = ∇_θ J(θ) + β_t d_{t-1}, (8.29)

其中β_t是一个系数，其大小控制我们应该将多少方向d_{t-1}加回到当前搜索方向。

如果d_t^⊤ H d_{t-1} = 0，则两个方向d_t和d_{t-1}被定义为共轭，其中H是Hessian矩阵。

施加共轭性的直接方法需要计算H的特征向量来选择β_t，这不满足我们为大型问题开发一种比牛顿法计算上更可行的方法的目标。我们能否在不进行这些计算的情况下计算共轭方向？幸运的是，答案是肯定的。

计算β_t的两种流行方法是

- 1. Fletcher-Reeves:
  
  $$\beta_t = \frac{\nabla_{\boldsymbol{\theta}} J(\boldsymbol{\theta}_t)^\top \nabla_{\boldsymbol{\theta}} J(\boldsymbol{\theta}_t)}{\nabla_{\boldsymbol{\theta}} J(\boldsymbol{\theta}_{t-1})^\top \nabla_{\boldsymbol{\theta}} J(\boldsymbol{\theta}_{t-1})}$$ (8.30)
  
- 2. Polak-Ribiére:
  
  $$\beta_t = \frac{(\nabla_{\boldsymbol{\theta}} J(\boldsymbol{\theta}_t) - \nabla_{\boldsymbol{\theta}} J(\boldsymbol{\theta}_{t-1}))^\top \nabla_{\boldsymbol{\theta}} J(\boldsymbol{\theta}_t)}{\nabla_{\boldsymbol{\theta}} J(\boldsymbol{\theta}_{t-1})^\top \nabla_{\boldsymbol{\theta}} J(\boldsymbol{\theta}_{t-1})}$$ (8.31)

对于二次曲面，共轭方向确保沿先前方向的梯度幅度不会增加。因此，我们停留在先前方向的最小值处。结果，在$k$维参数空间中，共轭梯度方法最多需要$k$次线搜索即可达到最小值。共轭梯度算法如算法8.9所示。

### 算法8.9 共轭梯度方法

```
Require: Initial parameters $\boldsymbol{\theta}_0$
Require: Training set of $m$ examples
Initialize $\boldsymbol{\rho}_0 = \mathbf{0}$
Initialize $g_0 = 0$
Initialize $t = 1$
while stopping criterion not met do
  Initialize the gradient $\boldsymbol{g}_t = \mathbf{0}$
  Compute gradient: $\boldsymbol{g}_t \leftarrow \frac{1}{m} \nabla_{\boldsymbol{\theta}} \sum_i L(f(\boldsymbol{x}^{(i)}; \boldsymbol{\theta}), \boldsymbol{y}^{(i)})$ 
  Compute $\beta_t = \frac{(\boldsymbol{g}_t - \boldsymbol{g}_{t-1})^\top \boldsymbol{g}_t}{\boldsymbol{g}_{t-1}^\top \boldsymbol{g}_{t-1}}$ (Polak-Ribiére)
  (Nonlinear conjugate gradient: optionally reset $\beta_t$ to zero, for example if $t$ is a multiple of some constant $k$, such as $k = 5$)
  Compute search direction: $\boldsymbol{\rho}_t = -\boldsymbol{g}_t + \beta_t \boldsymbol{\rho}_{t-1}$
  Perform line search to find: $\epsilon^* = \operatorname{argmin}_\epsilon \frac{1}{m} \sum_{i=1}^m L(f(\boldsymbol{x}^{(i)}; \boldsymbol{\theta}_t + \epsilon \boldsymbol{\rho}_t), \boldsymbol{y}^{(i)})$ 
  (On a truly quadratic cost function, analytically solve for $\epsilon^*$ rather than explicitly searching for it)
  Apply update: $\boldsymbol{\theta}_{t+1} = \boldsymbol{\theta}_t + \epsilon^* \boldsymbol{\rho}_t$
  $t \leftarrow t + 1$
end while
```

### 非线性共轭梯度：

到目前为止，我们讨论了应用于二次目标函数的共轭梯度方法。当然，本章的主要兴趣是探索用于训练神经网络和其他相关深度学习模型的优化方法，其中相应的
