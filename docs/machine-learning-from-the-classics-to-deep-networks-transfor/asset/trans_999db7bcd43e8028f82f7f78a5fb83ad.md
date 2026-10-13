

### 对数似然函数

$$
\ln p\left( \mathcal{X},\mathcal{K};\mathbf{\Xi},\mathbf{P} \right) = \sum\limits_{n = 1}^{N}\ln p(\mathbf{x}_{n},k_{n};\mathbf{\xi}_{k_{n}}) = \sum\limits_{n = 1}^{N}\ln\left( p(\mathbf{x}_{n}|k_{n};\mathbf{\xi}_{k_{n}})P_{k_{n}} \right).
$$

![Equation](images/B9780443292385000184/si219.png) (12.55)

#### 符号定义

我们使用以下符号表示法：

**Ξ** = [**ξ**[1]^(*T*), …, **ξ**[*K*]^(*T*)]^(*T*), **P** = [*P*[1], *P*[2], …, *P*[*K*]]^(*T*), 以及 **ξ**[*k*] = [**μ**[*k*]^(*T*), *σ*[*k*]²]^(*T*)。

![Equation](images/B9780443292385000184/si220.png)

换言之，通过 EM 算法需要估计的决定性参数包括所有高斯混合成分的均值和方差，以及相应的混合概率。

#### 后验概率

*   隐离散变量的后验概率由下式给出：

$$
P(k|\mathbf{x};\mathbf{\Xi},\mathbf{P}) = \frac{p(\mathbf{x}|k;\mathbf{\xi}_{k})P_{k}}{p(\mathbf{x};\mathbf{\Xi},\mathbf{P})},
$$

![Equation](images/B9780443292385000184/si221.png) (12.56)

*   其中

