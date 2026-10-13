

$p(\mathbf{x};\mathbf{\theta}) = C\exp\left( \sum\limits_{i \in I}\theta_{i}u_{i}(\mathbf{x}) \right) = \exp\left( \mathbf{\theta}^{T}\mathbf{u}(\mathbf{x}) - A(\mathbf{\theta}) \right),$

![Equation](images/B9780443292385000226/si166.png)

其中

$A(\mathbf{\theta}) = -\ln C = \ln \int \exp(\mathbf{\theta}^{(T)}\mathbf{u}(\mathbf{x})) \, d\mathbf{x},$

![Equation](images/B9780443292385000226/si167.png)

对于离散变量，积分变为求和；$A(\mathbf{\theta})$ 是一个凸函数，称为*对数配分函数*或*累积量生成函数*（问题 [16.14](#Chp016_805-853_B9780443292385000226.xhtml#o0110), [75,77]）。结果表明，$A(\mathbf{\theta})$ 的共轭函数，记为 $A^{*}(\mathbf{\mu})$，是 $p(\mathbf{x}; \mathbf{\theta}(\mathbf{\mu}))$ 的*负熵*函数，其中 $\mathbf{\theta}(\mathbf{\mu})$ 是在给定 $\mathbf{\mu}$ 值时，使共轭函数定义中的最大值成立的 $\mathbf{\theta}$ 值；我们称 $\mathbf{\theta}(\mathbf{\mu})$ 和 $\mathbf{\mu}$ 为对偶耦合（问题 [16.15](#Chp016_805-853_B9780443292385000226.xhtml#o0115)）。此外，

$\mathbb{E}[\mathbf{u}(\mathbf{x})] = \mathbf{\mu},$

![Equation](images/B9780443292385000226/si172.png)

其中期望是关于 $p(\mathbf{x}; \mathbf{\theta}(\mathbf{\mu}))$ 计算的。这是将 $\mathbf{\mu}$ 解释为均值参数向量的一个有趣视角；回顾第 [12.8.1](#Chp012_583-634_B9780443292385000184.xhtml) 节，这些均值参数定义了相应的指数分布。然后

$A(\mathbf{\theta}) = \max\limits_{\mathbf{\mu} \in \mathcal{M}}\left( \mathbf{\theta}^{T}\mathbf{\mu} - A^{*}(\mathbf{\mu}) \right),$

![Equation](images/B9780443292385000226/si174.png)(16.23)

