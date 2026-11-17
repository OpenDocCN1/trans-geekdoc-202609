

图 3.7 \(\kappa_a\) 作为 \(a\) 的函数及其拟合模型 \(\kappa = (\pi - 2)/a + 2\)。

![](img/f26d7f591c2a080d86425985301266a4_108_0.png)

图 3.8 不同 \(a\) 值下双指数分布与 log-cosh 的对比。

![](img/f26d7f591c2a080d86425985301266a4_108_1.png)

为选择适当的 \(a\) 值，我们回到第 2 章中的图 2.8，该图显示了 \(L_1\) 和 \(L_2\) 的损失与梯度。可以对 log-cosh 作为 \(a\) 的函数生成类似的图表。使用相同的数据来找到位置参数 \(\theta\)，即 \(\{0, 3, 5, 7, 10\}\)，结果如图 3.9 所示。注意，随着 \(a\) 从 1 增加到 100，连续损失变为分段线性，而连续梯度变为阶梯式连续。很明显，log-cosh 损失在一端表现类似于 \(L_2\)，在另一端表现类似于 \(L_1\)。但是，不建议使用大于 10 的 \(a\) 值，因为这可能会在梯度下降中引入收敛问题。因此，log-cosh 损失函数应始终以其最一般形式使用，即

```
LC loss = \(\frac{1}{a} \sum_{i=1}^n \log(\cosh(ar_i))\)
```

机器学习任务中 \(a\) 的典型值设置为 1、1.5、2、5 或 10。对于线性回归，建议设置 \(a = 2\)，原因将在第 4 章中说明。请注意，\(a\) 不像 Huber 中的 \(\delta\) 那样依赖于数据。它仅取决于所执行的机器学习任务类型。线性回归中 log-cosh 估计的标准误差可以使用第 3.6 节中概述的相同程序获得。

![](img/f26d7f591c2a080d86425985301266a4_109_0.png)

![](img/f26d7f591c2a080d86425985301266a4_109_1.png)

![](img/f26d7f591c2a080d86425985301266a4_109_2.png)

![](img/f26d7f591c2a080d86425985301266a4_109_3.png)

图 3.9 不同 \(a\) 值下 LC 损失与梯度的对比。对于线性回归，建议设置 \(a = 2\)。

## 3.9 总结

log-cosh 损失函数或许是机器学习中最重要的损失函数之一，因为它不仅提供鲁棒性，还具备允许进行详尽数学处理的所有相关正则性条件。在本章中，已识别出损失函数产生的分布，随后对损失函数进行了极大似然推导。还给出了其统计特性及标准误差的计算方法。log-cosh 的标准误差与最小二乘法进行了比较，结果显示对于含有异常值的数据集，其标准误差小于最小二乘法；对于无异常值的数据集，两者相似。基于详细的分析，有充分理由主张使用通用 log-cosh 损失来替代机器学习中许多其他损失函数。

## Problems

### 3.1

证明与 log-cosh 损失相关的 CDF（由以下公式给出）是正确的，方法是对其求导以生成 PDF。（提示：你可能需要用到恒等式 \(\sinh^2(x) + 1 = \cosh^2(x)\)。）

```
F_X(x) = \frac{1}{2} + \frac{1}{\pi} \arctan(\sinh(x)) ,
```

### 3.2

使用逆 MLE 程序找到与 M-loss = \(\sum_{i=1}^n \frac{1}{2} \log(\cosh(2x))\) 相关的分布。

使用以下步骤。
- a) 使用 \(f(x) = e^{-\rho(x)}/\kappa\) 找到分布的形式。
- b) 通过将结果从 \(-\infty\) 积分到 \(\infty\) 来找到归一化常数 \(\kappa\)。

### 3.3

使用逆 MLE 程序推导 Huber 分布。以下给出了前几个步骤，起始项为：

\(\rho_H(x) = \begin{cases} x^2/2 & \text{if } |x| \le \delta \\ \delta \left( |x| - \frac{\delta}{2} \right) & \text{if } |x| > \delta \end{cases}\)

应用上述逆 MLE 规则得到

\(f_X(x) = \frac{1}{\kappa} e^{-\rho_H(x)} = \frac{1}{\kappa} \begin{cases} e^{-x^2/2} & \text{if } |x| \le \delta \\ e^{-\delta \left( |x| - \frac{\delta}{2} \right)} & \text{if } |x| > \delta \end{cases}\)

剩下的步骤仅包括通过对不同区域进行积分并累加数值来找到 \(\kappa\) 的值。使用 \(\delta = 1.345\) 来简化计算。绘制分布图并将其与图 3.5 中的分布进行比较。使用 \(\delta = 0.1\) 和 \(\delta = 10\) 重新做此题。两个图中哪一个尾部更重？哪一个对异常值更鲁棒？

### 3.4 (项目)

在本项目中，你将使用通用 log-cosh 损失的稳健回归来估计数据集的斜率和截距，并将其与 Python 库 sklearn.linear_model 中实现的 Huber 方法进行比较。
- a) 加载 Python 库。

```
import numpy as np
from sklearn.linear_model import HuberRegressor
import matplotlib.pyplot as plt
from scipy.optimize import minimize
```
- b) 手动创建比利时电话数据集。

```
X = np.linspace(1950, 1973, 24).reshape(-1, 1)
y = np.array([ 0.44, 0.47, 0.47, 0.59, 0.66, \
    0.73, 0.81, 0.88, 1.06, 1.2 , \
    1.35, 1.49, 1.61, 2.12, 11.9 , \
    12.4 , 14.2 , 15.9 , 18.2 , 21.2 , \
    4.3 , 2.4 , 2.7 , 2.9 ])
```
- c) 定义通用 log-cosh 损失。

```
logcosh = lambda x: np.logaddexp(x, -x) - np.log(2)
def residual(b,x,y):
    residual_y = y-np.matmul(x,b)
    return residual_y
def LC(beta):
    ri = residual(beta,x,y)
    rho = (1/a)*logcosh(a*ri)
    loss = np.sum(rho)
    return loss
```
- d) 在 x 矩阵中创建一列 1。

```
column_ones = np.ones((24, 1))
x = np.hstack((column_ones, X))
```
- e) 使用 log-cosh 找到斜率和截距。

```
initbeta = np.array([0., 0.])
a = 2
minval = minimize(LC,initbeta)
beta = minval.x
```
- f) 绘制结果。

```
abline = np.zeros(x.shape[0])
for i in range(x.shape[0]):
    abline[i] = beta[0]+beta[1]*x[i,1]
plt.plot(x[:,1],abline)
plt.scatter(x[:,1],y)
plt.show()
```
- g) 使用不同的鲁棒系数 \(a\) 值重新运行。评论结果。
- h) 运行 Huber 回归器。将 \(\delta\)（称为 epsilon）从 4.0 调整到 0.1 以确定其影响。Huber 方法的此实现是否令人满意？

```
X = np.linspace(0, 23, 24).reshape(-1, 1)
huber = HuberRegressor(epsilon=4.0)
huber.fit(X, y)
y_pred = huber.predict(X)
plt.scatter(X+1950, y, color='blue', \
    label='Data points')
plt.plot(X+1950, y_pred, color='red', \
    label='Huber Regressor')
plt.xlabel('X')
plt.ylabel('y')
plt.legend()
plt.title('Huber Regressor with Outliers')
plt.show()
```

### 3.5 (项目)

在本项目中，你将使用最小二乘法对 Swiss 数据集求解估计值和标准误差。数据本身已在表 3.1 中提供。必须创建名为 swiss.csv 的文件以配合以下 Python 代码使用。
- a) 以下代码可用于导入库。

```python
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
from scipy.optimize import minimize
```
- b) Swiss 数据集可读入以创建 **X** 和 **y** 值，如下所示：

```python
swiss = pd.read_csv("swiss.csv")
swiss['ones'] = 1
X = np.array(swiss.drop(["Fertility"], axis=1))
Y = np.array(swiss["Fertility"])
```
- c) LS 代码如下：

```python
def LS(beta):
    ri = Y-np.matmul(X,beta)
    rho = ri*ri/2
    loss = np.sum(rho)
    return loss
```
- d) 以下代码可用于生成估计值。

```python
# Initialize betaLS
initbetaLS = np.array([-0.1,-0.1,-0.1,0.1,0.1,-0.1])
# Minimize the LS loss function
model = minimize(LS, initbetaLS, method='BFGS')
# Extract the estimates
betaLS = model.x
col_names = swiss.columns
print("Estimates:")
for i in range(len(betaLS)-1):
    print(col_names[i+1],f"{betaLS[i]:.3f}")
print(" (Intercept)",f"{betaLS[len(betaLS)-1]:.3f}")
```
- e) 为了获得标准误差，可以使用公式 (3.6.2)-(3.6.4) 中给出的表达式。

```python
resid = Y-np.matmul(X,betaLS)
n = X.shape[0]
p = X.shape[1]
d = p - 1
sigma2 = np.sum((resid-np.mean(resid))**2) / (n-d-1)
C = np.linalg.inv(np.matmul(X.T,X))
se2 = sigma2*np.diag(C)
```

