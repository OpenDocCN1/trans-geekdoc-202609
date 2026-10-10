
```
$J = f(\beta_{\mu}, \beta_{\nu}, \beta_{\zeta})$
```

微积分学指出，当函数的导数 $df/dx$ 为 0 时，函数 $f(x)$ 最小。$J$ 是一个多元函数，因此我们必须取偏导数。

为了获得 $J$ 的最小值，我们必须尝试不同的 $\beta_{\mu}$、$\beta_{\nu}$ 和 $\beta_{\zeta}$ 的值。我们将尝试的 $\beta_{\mu}$、$\beta_{\nu}$ 和 $\beta_{\zeta}$ 的不同值通过以下策略来确定：

- 我们设置一个下阈值，如果我们获得了一个良好的 $J$ 值，就认为我们找到了最小值。这是因为在执行浮点运算时，我们可能永远无法达到导数为 0 的点。为了演示这一点，假设阈值为 0。
- 我们为 $\beta_{\mu}$ 和 $\beta_{\nu}$ 设置初始值。假设我们将每个 $\beta_{\mu}$、$\beta_{\nu}$ 和 $\beta_{\zeta}$ 的初始值都为 2。
- 我们计算这组 $\beta_{\mu}$、$\beta_{\nu}$ 和 $\beta_{\zeta}$ 对应的 $J$ 值。

## 逻辑回归

如果 `J <=` 阈值，我们停止并将 `β0'`、`β1'` 和 `β2'` 的值视为我们找到最佳估计点。

如果 `J >` 阈值，我们计算 `β0'`、`β1'` 和 `β2'` 的新值：

```
$$\beta_{0'} = \beta_{0} - \alpha \frac{\delta J}{\delta \beta_{0}}$$ 其中 $\frac{\delta J}{\delta \beta_{0}}$ 是 $J$ 对 $\beta_{0}$ 的偏导数，$\alpha$ 是一个称为学习率的超参数。
```

```
$$\beta_{1'} = \beta_{1} - \frac{\delta J}{\delta \beta_{1}}$$ 其中 $\frac{\delta J}{\delta \beta_{1}}$ 是 $J$ 对 $\beta_{1}$ 的偏导数
```

```
$$\beta_{2'} = \beta_{2} - \frac{\delta J}{\delta \beta_{2}}$$ 其中 $\frac{\delta J}{\delta \beta_{2}}$ 是 $J$ 对 $\beta_{2}$ 的偏导数
```

我们重复步骤 3、4 和 5。让我们用一些数字来理解前面的策略。假设我们从 `β0', β1', β2` 设置为 2 开始。让我们考虑 `β0', β1', β2` 设置为 2。我们可以计算 `J`。由于 `J >` 阈值，我们需要计算 `β0', β1'` 的新值。对于 `β0', β1'` 和 `β2`，根据图 4.6，我们得到 `J = 7.58`。由于 `J >` 阈值，我们需要再次计算 `β0', β1'` 和 `β2` 的值。

## 逻辑回归

我们将从二分类（即目标变量可以取两个值——0 和 1）开始讨论，稍后将其扩展到多分类。

当我们使用线性模型来预测类别变量时，它被称为逻辑回归模型（Logistic Regression model）。换句话说，使用线性方法解决分类模型的算法就称为逻辑回归算法。

在逻辑回归算法中，我们将预测目标变量（类别型）的问题转换为预测目标变量出现概率的问题。现在，概率是 0 到 1 之间的一个值，这使得预测类别目标变量的问题变成了预测一个连续变量的问题。

让我们通过一个例子来理解这一点。假设我们的问题是预测一条短信是否为垃圾邮件。我们需要预测两个类别：垃圾邮件（SPAM）和非垃圾邮件（NOT SPAM）。现在，我们将垃圾邮件标记为 1，将非垃圾邮件标记为 0。我们的问题是预测 1 或 0。然而，我们将问题改变为了预测短信为垃圾邮件（SPAM）的概率。换句话说，我们的目标变量是 $P_{y}(y=1)$。由于这是一个概率，$P(y=1)$ 可以取 0 到 1 之间的任何值。因此，它是一个连续变量。在获得值后，我们考虑一个阈值。如果 $P_{y}(y=1)>$ 阈值，我们认为 $y=1$（在此情况下为垃圾邮件）。如果 $P_{y}(y=1)\le$ 阈值，则 $y=0$（在此情况下为非垃圾邮件）。

因此，我们正在使用线性回归方法来进行预测。通过获取预测结果，我们将预测值与阈值比较以得到预测的二分类。

### Sigmoid 函数

对于逻辑回归算法，我们需要一个输出 0 到 1 之间值的函数。实现此功能的函数是 Sigmoid 函数。函数的形式如下：

```
$$\sigma(t) = \frac{1}{1+e^{-t}}$$
```

在这里，t 可以取 $-\infty$ 到 $+\infty$ 之间的值。

当 $t=-\infty$ 时，$e^{-t}=e^{-(-\infty)}=\infty$。因此，$\sigma(t)=\frac{1}{1+e^{-t}}=\frac{1}{1+\infty}=\frac{1}{\infty}=0$。

当 $t=+\infty$ 时，$e^{-t}=e^{(+\infty)}=0$。因此，$\sigma(t)=\frac{1}{1+e^{-t}}=\frac{1}{1+0}=\frac{1}{1}=1$。

# 掌握机器学习分类算法

如果我们绘制不同 t 值对应的 $\sigma(t)$ 值的图表，我们得到如图 4.8 所示的图：

![](img/11af2c4c7dddfed06ed008516c0c6dfb_123_0.png)

因此，Sigmoid 函数始终取 0 到 1 之间的值。

我们将面临一个具有一个或多个特征（或独立变量）以及 1 个目标变量（或因变量）的分类问题。因此，问题的线性形式如下：

$y = a_0 + a_1x_1 + a_2x_2 + \dots + a_nx_n$

应用 Sigmoid 函数，我们将得到如下：

$\sigma(y) = \frac{1}{1+e^{-y}} = \frac{1}{1+e^{-(a_0+a_1x_1+\dots+a_nx_n)}}$

因此，对于每一个数据点，我们得到一个 0 到 1 之间的值。为了进行预测，我们将其公式化：

$y = \begin{cases} 1, \text{如果 } \sigma(y) > 0.5 \\ 0, \text{如果 } \sigma(y) \le 0.5 \end{cases}$

在这里，我们将阈值设置为 0.5。根据我们的问题，我们可以将阈值设置为 0 到 1 之间的任何其他值。

现在我们的数据集中有很多数据点，共 m 个数据点。对于每个数据点，我们得到如下：

$\sigma(y_i) = \frac{1}{1+e^{-y_i}} = \frac{1}{1+e^{-(a_0+a_1x_1+\dots+a_nx_i)}}$ 这里 $i$ 从 1 变化的 m。

## 逻辑回归算法的代价函数

与线性回归算法不同，我们不能使用 MSE（均方误差）等指标作为逻辑回归算法的代价函数。我们需要设计一个代价函数，以便衡量我们的二分类是否准确。一旦确定了代价函数，我们就可以应用梯度下降算法来最小化代价函数，以获得最优模型。

我们现在知道数据点的预测如下：

```
$$\sigma(y_i) = \frac{1}{1 + e^{-Y_i}} = \frac{1}{1 + e^{-(a_0 + a_1x_1 + \dots + a_nx_{n_l})}}$$
```

我们将 $\sigma(y_j)$ 称为 $(p_j)$。因此，我们得到如下：

```
$$p_i = \sigma(y_i) = \frac{1}{1 + e^{-Y_i}} = \frac{1}{1 + e^{-(a_0 + a_1x_1 + \dots + a_nx_{n_l})}}$$
```

逻辑回归的代价函数给出如下：

$$J = -\frac{1}{m} \sum_{i=1}^{m} [y_i \log(p_i) + (1-y_i) \log(1-p_i)]$$

让我们理解这个代价函数。注意概率只能取 0 到 1 之间的值。$(p)$ 和 $(1-p)$ 分别接近 0 和 1。如果 $y_i=1$ 且 $p_i$ 接近 1，$\log(p_i)$ 接近 0；如果 $y_i=1$ 且 $p_i$ 接近 0，$-\log(p_i)$ 是一个很大的数。同样，如果 $y_i=0$ 且 $p_i$ 接近 1，$\log(1-p_i)$ 接近 0；如果 $y_i=0$ 且 $p_i$ 接近 0，$-\log(1-p_i)$ 是一个很大的数。

为了保留代价函数的特性，可以将代价函数写为：

$$J = -\frac{1}{m} \sum_{i=1}^{m} [y_i \log(\hat{y}_i) + (1-y_i) \log(1-\hat{y}_i)]$$

这可以通过替换 $y_i = a_0 + a_1x_1 + a_2x_2 + \dots + a_nx_n$ 进一步扩展：

$$J = -\frac{1}{m} \sum_{i=1}^{m} [y_i \log(\sigma(y_i)) + (1-y_i) \log(1-\sigma(y_i))]$$

这个代价函数被称为对数损失（Log-Loss）函数。Sigmoid 函数被称为逻辑函数。我们得到了用于逻辑回归算法的公式。我们需要通过改变系数来最小化 $J$，每次迭代得到的系数为：

$a_i = a_i - \alpha \frac{\partial J}{\partial a_i}$ 其中 $\alpha$ 是学习率。

我们在 Python 中使用 `sympy` 库提供了一个简单的方法来寻找 $\frac{\partial J}{\partial a_i}$，如图 4.9 所示：

```python
from sympy import symbols, log, exp, diff

a0, a1, a2, x1, x2 = symbols('a0 a1 a2 x1 x2')

### 注意：由于 OCR 文本存在乱码，此处基于标准代价函数进行逻辑推导
### (此处代码逻辑展示了如何求导)
```

### (注：原文中 log 之后存在 OCR 错误，此处已根据标准逻辑回归公式进行逻辑对齐)

### 应用逻辑回归算法

让我们运行一个将逻辑回归算法应用于分类问题的简单示例。

我们对任何地方的温度进行了标记，分类为 0 表示热（HOT），1 表示冷（COLD），如图 4.10 所示。

| 温度 (x1) | 天气 (y) |
|---|---|
| 40 | 0 |
| 2 | 1 |
| -3 | 1 |
| 10 | 1 |
| 20 | 0 |
| 30 | 0 |
| 4 | 1 |
| 7 | 1 |
| 22 | 0 |
| 50 | 0 |
| 60 | 0 |
| -5 | 1 |
| 4 | 1 |
| 6 | 1 |
| 32 | 0 |

> 0 - HOT
> 1 - 冷

图 4.10：用于分类的天气数据

因此，我们有独立变量 ($x_1$)，因变量是 $y$。因此，我们需要建立如下的线性关系：

$y = a_0 + a_1x_1$

由于这是一个分类问题，我们将构建如下的 Sigmoid 函数：

$$\sigma(y) = \frac{1}{1+e^{-y}} = \frac{1}{1+e^{-(a_0+a_1x_1)}}$$

你可以按照提供的 Python 程序来创建逻辑回归模型：

```python
X = [40, 2, -3, 10, 20, 30, 4, 7, 22, 50, 60, -5, 4, 6, 32]
y = [0, 1, 1, 1, 0, 0, 1, 1, 0, 0, 0, 1, 1, 1, 0]

import pandas as pd
```

```python
df = pd.DataFrame({'X':X, 'y':y})

from sympy import *
a0, a1, x1 = symbols('a0, a1, x1')

J = ((a0 + (a1*x1)) * log(1 / (1 + exp(-(a0 + (a1*x1))))) + \
     ((1 - (a0 + (a1*x1))) * log(1 - (1 / (1 + exp(a0 + (a1*x1)))))))
diff_a0 = diff(J, a0)
diff_a1 = diff(J, a1)

a0_val = 5
a1_val = 5
alpha = 0.001
threshold = 0
testList = []

for c in range(100):
    # 计算代价 Cost
    Cost = 0
    for i in range(len(df)):
        Cost += J.eval(subs={a0: a0_val, a1: a1_val, x1: df.loc[i, 'X']})

    Cost *= (1 / (len(df)))

    print("Iteration: %d, Cost - %f" % (c, Cost))
    print("\ta0 - %f, a1 - %f" % (a0_val, a1_val))
    testList.append({'Cost': Cost, 'a0': a0_val, 'a1': a1_val})
    if Cost < threshold:
        break

### 偏导
sumdiff = 0
sumdiff_x1 = 0
for i in range(len(df)):
    sumdiff += diff_a0.evalf(subs = {a0: a0_val, a1: a1_val, x1: df.loc[i, 'X']})
    sumdiff_x1 += diff_a1.evalf(subs = {a0: a0_val, a1: a1_val, x1: df.loc[i, 'X']})
```

```python
del_j_a0 = ((1 / (len(df))) * sumdiff)
del_j_a1 = ((1 / (len(df))) * sumdiff_x1)
```

### 更新参数

a0_val = a0_val - (alpha * del_j_a0)

a1_val = a1_val - (alpha * del_j_a1)

Iteration: 0, Cost - 14766.723588

a0 - 5.000000, a1 - 5.000000

Iteration: 1, Cost - 876.45461

a0 - 3.053107, a1 - 1.037362

Iteration: 2, Cost - 170.045108

a0 - 2.396249, a1 - -0.545897

Iteration: 3, Cost - 31.870917

a0 - 2.633374, a1 - 0.148471

Iteration: 4, Cost - 6.492363

a0 - 2.486089, a1 - -0.143966

Iteration: 5, Cost - 2.124769

a0 - 2.499813, a1 - -0.026896

Iteration: 41, Cost - 0.049555

a0 - 1.614739, a1 - -0.034913

Iteration: 42, Cost - 0.027046

a0 - 1.596394, a1 - -0.034430

Iteration: 43, Cost - 0.005170

a0 - 1.578308, a1 - -0.033954

Iteration: 44, Cost - -0.016089

a0 - 1.560479, a1 - -0.033498

我们可以如下测试模型：

```python
def testWeather(test):
    THRESHOLD = 0.8
    returnValue = "HOT"
    if test > THRESHOLD:
        returnValue = "COLD"
    return returnValue
```

$Y = (1 / (1 + exp(-(a0 + (a1*x1))))) Y.evalf(subs={a0: testList[-2][0], a1: testList[-2][1], x1: 43})$

testWeather(test)

'HOT'

$test = Y.evalf(subs={a0: testList[-2][0], a1: testList[-2][1], x1: 43})$

testWeather(test)

'COLD'

注意，我们使用了 0.8 的阈值来进行决策。梯度下降算法和逻辑回归算法是神经网络的基础。

### 决策边界

现在我们创建了逻辑回归模型，为所有数据点绘制 Sigmoid 函数。我们表示 $\tilde{p}=\sigma(y)$。因此，$p$ 是分类为 1 的概率，$1-\tilde{p}$ 是分类为 0 的概率。我们使用以下代码计算 $\tilde{p}$ 和 $(1-\tilde{p})$ 的值并将其添加到 $x_i$ 值的 dataframe 中：

```python
s = (1 / (1 + exp(-(a0 + (a1*x1))))
sList = []
tList = []
for i in range(len(df)):
    P = s.evalf(subs={a0: testList[-2][0], a1: testList[-2][1], x1: df.loc[i, 'X']})
    sList.append(P)
    tList.append(1 - P)

df['P'] = sList
df['1 - P'] = tList
df = df.sort_values('X')
```
