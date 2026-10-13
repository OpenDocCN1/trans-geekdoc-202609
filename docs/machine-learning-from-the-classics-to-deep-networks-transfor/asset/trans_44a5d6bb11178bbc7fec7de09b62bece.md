

## 高斯-伽马分布

$$p(\mu,\beta;\lambda,\mathbf{v}) = \mathcal{N}\left( \mu \middle| \frac{v_{2}}{\lambda},{(\lambda\beta)}^{- 1} \right)\text{Gamma}\left( \beta \middle| \frac{\lambda + 1}{2},\frac{v_{1}}{2} - \frac{v_{2}^{2}}{2\lambda} \right),$$

这被称为**高斯-伽马分布**，其中高斯分布的均值为 $\mu_{0} = \frac{v_{2}}{\lambda}$，方差为 $\sigma_{\mu}^{2} = (\lambda\beta)^{-1}$，而伽马概率密度函数的定义参数为 $a = \frac{\lambda + 1}{2}$ 和 $b = \frac{v_{1}}{2} - \frac{v_{2}^{2}}{2\lambda}$。[图 12.11](#Chp012_583-634_B9780443292385000184.xhtml#f0075) 展示了公式 [(12.84)](#Chp012_583-634_B9780443292385000184.xhtml#deq116) 中高斯-伽马分布的等高线图。

![Figure 12.11 Contour plots of the Gaussian–gamma distribution with parameter values λ=2, v1=4, v2=0.](images/B9780443292385000184/gr011.jpg)

**图 12.11** 参数值为 $\lambda=2$、$v_{1}=4$、$v_{2}=0$ 的高斯-伽马分布等高线图。

## 多元高斯情况

对于更一般的多元高斯情况，$\mathcal{N}(\mathbf{x}|\boldsymbol{\mu}, \Sigma)$，结果表明它也呈指数形式，其共轭先验为高斯-威沙特形式（问题 [12.13](#Chp012_583-634_B9780443292385000184.xhtml#o0150)），即

$$p(\boldsymbol{\mu}, \mathbf{Q}; \boldsymbol{\mu}_{0}, \lambda, \mathbf{W}, \nu) = \mathcal{N}(\boldsymbol{\mu}|\boldsymbol{\mu}_{0}, (\lambda \mathbf{Q})^{-1})\mathcal{W}(\mathbf{Q}|\mathbf{W}, \nu),$$

其中 $\mathbf{Q} = \Sigma^{-1}$。

## 示例 12.6

我们现在将注意力转向离散变量，将展示多项式分布呈指数形式，且其共轭先验由狄利克雷分布给出。

