

$$
\left( \sum\limits_{n = 1}^{N}x_{n}^{2} \right)\widehat{\theta} = \sum\limits_{n = 1}^{N}y_{n}x_{n},\quad \text{or}\quad \widehat{\theta} = \frac{\sum_{n = 1}^{N}y_{n}x_{n}}{\sum_{n}^{N}x_{n}^{2}}.
$$

![Equation](images/B9780443292385000093/si59.png)

一种更通用的书写公式 [(3.13)](#Chp003_65-117_B9780443292385000093.xhtml#deq16) 的方法是通过所谓的输入矩阵 `X`，它被定义为 `N × (l + 1)` 矩阵，其行是（扩展）回归向量 `x[n]^(T)`，`n = 1, 2, …, N`，表示为

```
X := [x_1^T; x_2^T; ...; x_N^T] = [x_11 ... x_1l 1; x_21 ... x_2l 1; ...; x_N1 ... x_Nl 1].
```

![Equation](images/B9780443292385000093/si62.png) (3.14)

然后很容易看出，公式 [(3.13)](#Chp003_65-117_B9780443292385000093.xhtml#deq16) 可以写成

```
(X^T X) \hat{\theta} = X^T y,
```

![Equation](images/B9780443292385000093/si63.png) (3.15)

其中

