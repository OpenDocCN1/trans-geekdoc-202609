
## 反向传播算法推导

### 输出层误差项定义

$$
\delta_{nj}^{L} = \frac{\partial J_{n}}{\partial z_{nj}^{L}}.
$$

![Equation](images/B978044329238500024X/si143.png) (18.19)

### 1. 均方误差损失函数

$$
J_{n} = \frac{1}{2}\sum_{k = 1}^{k_{L}}\left( f(z_{nk}^{L}) - y_{nk} \right)^{2}.
$$

![Equation](images/B978044329238500024X/si144.png) (18.20)

### 2. 输出层梯度计算

因此，

$$
\delta_{nj}^{L} = (\hat{y}_{nj} - y_{nj}) f'(z_{nj}^{L}) = e_{nj} f'(z_{nj}^{L}), \quad j = 1, 2, \dots, k_{L},
$$

![Equation](images/B978044329238500024X/si145.png) (18.21)

其中 $f'$ 表示 $f$ 的导数，$e_{nj}$ 是第 $n$ 个样本第 $j$ 个输出变量的误差。注意对于输出层，梯度 $\delta_{nj}^{L}$ 的计算是直接的。

### 3. 隐藏层梯度计算 ($r < L$)

由于层间的逐层依赖关系，$z_{nj}^{r-1}$ 的值影响下一层的所有值 $z_{nk}^{r}$（$k = 1, 2, \dots, k_{r}$）。利用链式法则求导，我们得到：
