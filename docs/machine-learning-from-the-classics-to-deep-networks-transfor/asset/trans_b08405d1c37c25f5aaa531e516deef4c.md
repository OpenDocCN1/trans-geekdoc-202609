

### 练习

#### 12.10
证明：对于已知的 $\boldsymbol{\Sigma}$，$\mathcal{N}(\mathbf{x}|\boldsymbol{\mu}, \boldsymbol{\Sigma})$ 属于指数族形式，且其共轭先验也是高斯分布。

#### 12.11
证明：多元高斯分布关于精度矩阵 $\mathbf{Q}$ 的共轭先验是 Wishart 分布。

#### 12.12
证明：单变量高斯分布 $\mathcal{N}(x|\mu, \sigma^2)$ 关于均值和精度 $\beta = \frac{1}{\sigma^2}$ 的共轭先验是高斯-伽马乘积形式

$$
p(\mu, \beta; \lambda, \mathbf{v}) = \mathcal{N}\left( \mu \middle| \frac{v_2}{\lambda}, (\lambda \beta)^{-1} \right) \text{Gamma}\left( \beta \middle| \frac{\lambda + 1}{2}, \frac{v_1}{2} - \frac{v_2^2}{2\lambda} \right),
$$

其中 $\mathbf{v} := [v_1, v_2]^T$。

#### 12.13
证明：多元高斯分布 $\mathcal{N}(\mathbf{x}|\boldsymbol{\mu}, \mathbf{Q}^{-1})$ 关于均值和精度矩阵 $\mathbf{Q}$ 的共轭先验是高斯-Wishart 乘积形式。

#### 12.14
证明：分布

$$
P(x|\mu) = \mu^x (1 - \mu)^{1-x}, \quad x \in \{0, 1\},
$$

属于指数族形式，并推导其关于 $\mu$ 的共轭先验。

#### 12.15
证明：在一组经验期望的约束下，通过最大化相应熵来估计未知 PDF，得到的 PDF 属于指数族。

### 计算机练习

#### 12.16
在区间 $[0, 2]$ 内采样 $N = 20$ 个等间距点 $x[n]$。根据[示例 12.1](#Chp012_583-634_B9780443292385000184.xhtml#enun0015) 的非线性模型生成输出样本 $y[n]$，其中噪声方差设为 $\sigma_\eta^2 = 0.05$。

