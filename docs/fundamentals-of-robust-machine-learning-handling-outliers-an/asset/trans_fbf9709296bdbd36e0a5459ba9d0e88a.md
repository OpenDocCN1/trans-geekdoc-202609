


| | LSE | LAD | Huber |
|---|---|---|---|
| Intercept | −983.9 | −305.0 | −298.0 |
| Slope | 0.504 | 0.155 | 0.154 |
| δ | — | — | 0.269 |

### 2.10.2 与 LSE 和 LAD 的比较

我们比较了三种估计方法，即 LSE、LAD 和 Huber 方法，在比利时电话数据集上。估计值在表 2.2 中给出。对于 Huber，如前所述，δ 的最优选择取决于数据。在此情况下，最优值为 δ = 0.269。Huber 方法和 LAD 的结果非常相似，并且都与 LSE 截然不同，这与预期一致。

为了更好地理解 δ 的影响，请参考图 2.13 中的线性回归结果图。在此情况下，在 0 到 100 之间选择了 100 个不同的 δ 值。Huber 生成的 100 条线着色了由 LSE 和 LAD 界定的区域。这是预期的，因为在一个极端，Huber 方法退化为 LSE，而在另一个极端，它变为 LAD。同样，δ 取决于数据，但在实践中通常设置为默认值 δ = 1.345。

![](img/f26d7f591c2a080d86425985301266a4_84_0.png)

图 2.13 使用比利时电话数据集比较 LSE、LAD 和 Huber。LSE 和 LAD 结果构成了 Huber 结果的边界。

## 2.11 总结

本章介绍了用于线性回归的 \(L_1\)、\(L_2\) 和 Huber 损失函数。\(L_1\) 损失函数对异常值具有鲁棒性，但存在使其实践中难以使用的数学和数值问题。\(L_2\) 损失函数（产生普通最小二乘估计的方法）对异常值不耐受。Huber 方法结合了 \(L_1\) 和 \(L_2\) 损失函数的优点，并对异常值具有耐受性。然而，它也存在一些问题，即其二阶导数不连续，我们必须能够找到 \(\delta\) 的合适值，以及估计值本身。此外，较小的 \(\delta\) 值可能不适合使用梯度下降进行优化。在下一章中，将介绍另一种方法，它避免了 Huber 方法固有的问题，并在鲁棒机器学习中大有前途。

## 练习题

### 2.1 考虑以下小数据集。

| \(x_i\) | 0.10 | 0.20 | 0.30 | 0.40 | 0.50 | 0.60 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| \(y_i\) | 3.2 | 4.0 | 4.2 | 4.7 | 6.5 | 5.5 |

假设数据按以下模型建模：

\(\mathbf{y} = \beta_0 + \beta_1 \mathbf{x} + \boldsymbol{\epsilon}.\)

执行手动计算，或使用 Python，完成以下任务。

- a) 使用以下公式求最小二乘（LS）估计：

\(\hat{\beta}_1^{LS} = \frac{\sum_{i=1}^n (x_i - \bar{x})(y_i - \bar{y})}{\sum_{i=1}^n (x_i - \bar{x})^2}, \quad \text{and} \quad \hat{\beta}_0^{LS} = \bar{y} - \hat{\beta}_1^{LS} \bar{x},\)

其中 \(\bar{x}\) 和 \(\bar{y}\) 分别是各自变量的均值。

- b) 绘制点和 LS 回归直线。在图中标识斜率和截距。

- c) 在图中使用垂直线指示残差。残差之和是多少？

### 2.2 以下分布的 \(\mu\) 的最大似然估计量是什么？

\(f_\mu(x) = \frac{1}{1 + (x - \mu)^2}\)

### 2.3 位置问题的 \(L_2\) 损失函数由以下公式给出

\(L_2(\theta) = \frac{1}{2} \sum_{i=1}^n (x_i - \theta)^2.\)

梯度函数为

\(L'_2(\theta) = -\sum_{i=1}^n (x_i - \theta).\)

- a) 对于数据集 \(\boldsymbol{x} = \{1, 2, 3, 4, 5, 6, 7, 100\}\)，绘制损失函数和梯度函数。选择 0 到 30 之间的 \(\theta\) 值。
- b) 在最小值处的 \(\theta\) 值是多少，称为 \(\hat{\theta}^{LS}\)。

### 2.4 位置问题的 \(L_1\) 损失函数由以下公式给出

\(L_1(\theta) = \sum_{i=1}^n |x_i - \theta|.\)

梯度函数为

\(L'_1(\theta) = -\sum_{i=1}^n \text{sgn}(x_i - \theta).\)

- a) 对于数据集 \(\boldsymbol{x} = \{1, 2, 3, 4, 5, 6, 7, 100\}\)，绘制损失函数和梯度函数。选择 0 到 10 之间的 \(\theta\) 值。
- b) 在最小值处的 \(\theta\) 值是多少，称为 \(\hat{\theta}^{LAD}\)。

### 2.5 位置问题的 Huber 损失函数由以下公式给出

\(H(\theta) = \sum_{i=1}^n \rho_H(x_i - \theta),\)

其中

\(\rho_H(\theta) = \begin{cases} (x_i - \theta)^2 / 2 & \text{if } |(x_i - \theta)| \le \delta \\ \delta(|x_i - \theta| - \frac{\delta}{2}) & \text{if } |(x_i - \theta)| > \delta \end{cases}\)

梯度函数为

\(H'(\theta) = \sum_{i=1}^n \psi_H(x_i - \theta).\)

其中

\(\psi_H(\theta) = \begin{cases} (x_i - \theta) & \text{if } |(x_i - \theta)| \le \delta \\ -\delta & \text{if } (x_i - \theta) > +\delta \\ +\delta & \text{if } (x_i - \theta) < -\delta \end{cases}\)

- a) 设置 \(\delta = 1\)，并将函数 \(\rho_H(\theta)\)、\(\psi_H(\theta)\) 和 \(\psi'_H(\theta)\) 作为 \(r_i = x_i - \theta\) 的函数进行绘制。该函数是否为凸函数？
- b) 对于数据集 \(\boldsymbol{x} = \{1, 2, 3, 4, 5, 6, 7, 100\}\)，将 \(H(\theta)\) 作为 \(\theta\) 的函数进行绘制。选择 0 到 10 之间的 \(\theta\) 值。
- c) 对于数据集 \(\boldsymbol{x} = \{1, 2, 3, 4, 5, 6, 7, 100\}\)，将 \(H'(\theta)\) 作为 \(\theta\) 的函数进行绘制。选择 0 到 10 之间的 \(\theta\) 值。
- d) 计算数据集 \(\boldsymbol{x} = \{1, 2, 3, 4, 5, 6, 7, 100\}\) 的位置参数 Huber 估计值 \(\hat{\theta}^H\)。
- e) 使用 \(\delta = 10\) 和 \(\delta = 0.1\) 重复第 (d) 部分。在 \(\delta = 1\)、\(\delta = 10\) 和 \(\delta = 0.1\) 中，哪个 \(\delta\) 值最适合此数据集？

### 2.6 本题涉及机器学习中梯度下降的应用。假设目标是为简单线性回归问题最小化 \(L_2\) 损失函数，如下所示：

$$\hat{\beta}^{\text{LS}} = \arg\min_{\beta \in \mathbb{R}^2} \left[ \frac{1}{2} \sum_{i=1}^n (y_i - \mathbf{x}_i^T \beta)^2 \right].$$

最小二乘估计器的更新方程是什么？注意，它将采用以下形式：

$$\beta_j^{t+1} = \beta_j^t - \ell \times \frac{\partial f(\beta)}{\partial \beta_j}$$

其中 \(j = 0\) 或 \(1\)，\(\ell\) 是预定义的学习率，\(f(\beta)\) 是损失函数。

### 2.7（项目）在本项目中，你将使用 Huber 方法的稳健回归求解数据集的斜率和截距。

- a) 导入所需的库。

```
import numpy as np
from sklearn.linear_model import HuberRegressor
import matplotlib.pyplot as plt
```

- b) 创建类似于电话数据集的数据。

```
np.random.seed(0)
X = np.linspace(0, 23, 24).reshape(-1, 1)
y = np.array([ 0.44, 0.47, 0.47, 0.59, 0.66,
0.73, 0.81, 0.88, 1.06, 1.2 ,
1.35, 1.49, 1.61, 2.12, 11.9 ,
12.4 , 14.2 , 15.9 , 18.2 , 21.2 ,
4.3 , 2.4 , 2.7 , 2.9 ])
```

- c) 使用数据拟合 Huber 回归器。

```
huber = HuberRegressor(epsilon=4.0)
huber.fit(X, y)
slope = huber.coef_[0]
intercept = huber.intercept_
print("Slope=", f"{slope:.1f}", "Intercept=", f"{intercept:.1f}")
y_pred = huber.predict(X)
```

- d) 绘制结果。

```
plt.scatter(X, y, color='blue', label='Data points')
plt.plot(X, y_pred, color='red', label='Huber Regressor')
plt.xlabel('X')
plt.ylabel('y')
plt.legend()
plt.title('Huber Regressor with Outliers')
plt.show()
```

- e) 使用 \(\delta = 4, 1.345, \text{和 } 0.1\) 绘制结果（注意：epsilon 是 \(\delta\) 参数）。哪个 \(\delta\) 值产生了稳健解？解释为什么 \(\delta = 0.1\) 可能会是一个问题（提示：它是使 Huber 更接近 \(L_1\) 还是 \(L_2\)？）。

## 参考文献

Montgomery, D.C., Peck, E.A., and Vining, G.G. (2012). 线性回归分析导论（第4版）. Wiley.
Huber, P.J. and Ronchetti, E.M. (2009). 鲁棒统计学（第2版）. John Wiley and Sons.

## 3 对数双曲余弦损失函数

### 3.1 引言

在上一章中，我们介绍了 \(L_1\) 损失函数（更常被称为最小绝对偏差（LAD））和 Huber 损失函数，作为我们首次接触稳健估计量。在本章中，我们探讨了稳健类别中一个更近期的条目，即 log-cosh 损失函数，它是本书中将要介绍的稳健方法的核心。该损失函数属于关联稳健估计量类，因为与 Huber 一样，它也倾向于偏好中位数附近的解而不是均值。另一种观点是，它对数据集中的异常值更加耐受，因为关联估计量家族与 \(L_1\) 估计量相关。一个突出的特点是，它是一个单一的、可连续微分的函数，其性质是参数化的，因此具有估计器的所有理想属性，如凸性、一致性和渐近正态性。这与 Huber 损失形成对比，Huber 损失具有多个分段和不连续的二阶导数。

在本章中，我们将证明 log-cosh 损失函数优于机器学习中的其他稳健估计量。本章通过从第一原理推导（始于其分布）对 log-cosh 损失函数进行了详细和彻底的处理。然后，我们将研究偏差、方差和估计标准误等属性。我们还将使用位置和尺度参数探索基本 log-cosh 损失的各种扩展。最后，将展示 log-cosh 损失的一般 M-估计量形式是鲁棒机器学习的一种非常强大的工具。

### 3.2 Log-Cosh 的直观视图

为了直观地理解 log-cosh，我们需要回到 \(L_1\) 损失函数并找出其主要弱点。最小化该损失函数得到中位数作为估计值，将数据分为两半。然而，损失项存在一个折点，这导致一阶导数不连续且二阶导数未定义$^1$。这意味着损失函数的优化可能无法产生唯一解，且解可能需要除梯度下降以外的方法。事实上，\(L_2\) 今天被广泛使用的原因之一是 \(L_1\) 损失需要线性规划。

1 更准确地说，二阶导数在原点处为冲激函数，其他地方为零。

