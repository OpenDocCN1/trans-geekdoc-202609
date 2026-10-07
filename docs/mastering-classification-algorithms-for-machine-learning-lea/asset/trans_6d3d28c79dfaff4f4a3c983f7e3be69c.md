
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

# 偏导
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

# 更新参数

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

# 决策边界

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

| X | y | P | 1 - P |
|---|---|---|---|
| 11 | -5 | 0.8517300213465 | 0.1482699786535 |
| 2 | -3 | 0.8429271085189 | 0.1570728914811 |
| 1 | 2 | 0.8191250290119 | 0.1808749709888 |
| 6 | 4 | 0.8088402812548 | 0.1911597418745 |
| 12 | 4 | 0.8084025812548 | 0.1915974187452 |
| 13 | 6 | 0.7981193783705 | 0.2018802612895 |
| 7 | 7 | 0.7925393473549 | 0.2074606524507 |
| 3 | 10 | 0.7735494234048 | 0.2264505766952 |
| 4 | 20 | 0.7107096183215 | 0.2892903816785 |
| 8 | 22 | 0.6966339690534 | 0.3033660309466 |
| 5 | 30 | 0.6363799254212 | 0.3636200745788 |
| 14 | 32 | 0.6205203403658 | 0.3794796596342 |
| 0 | 40 | 0.5548156673591 | 0.4451843326409 |
| 9 | 50 | 0.4701865372324 | 0.5298134627676 |

