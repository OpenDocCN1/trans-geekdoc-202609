
*但既然* $g(x) = 3x + 2$ *则：*

$$g(x + x^{\mathbf{d}}) = g(x) + g'(x)x^{\mathbf{d}} \quad (5.61)$$

*4 使用 DN 在* $x = 2$ *处评估函数* $g(x)$ *，我们得到：*

$$g(x = 2) = (3 \cdot 2 + 2) + (3)x^{\mathbf{d}} \quad (5.62)$$

$$8 + (3)x^{\mathbf{d}} \quad (5.63)$$

*5 5.17 中的代码片段使用 Autograd 实现了该函数*

```python
1 import autograd.numpy as np
2 from autograd import grad
3 x = np.array([2.0], dtype=float)
4 def fl(x):
5     return 3*x + 2
6 grad_fl = grad(fl)
7 print(fl(x)) #> 8.0
8 print(grad_fl(x)) #> 3.0
```

图 5.17：Autograd

# SOL-127 CH.SOL-5.28. *答案如下：*

*1 如果我们从左到右遍历图* 5.9 *，我们将推导如下函数：*

$$g(x) = 5x^2 + 4x + 1 \quad (5.64)$$

*2 我们知道：*

$$g(x_1) = 5x^2 + 4x + 1 \quad (5.65)$$

$$g'(x_1) = 10x_1 + 4 \quad (5.66)$$

*现在我们使用 DN 展开该函数，得到：*

$$g(x + \mathbf{x\!d}) = 5 * (x + \mathbf{x\!d})^2 + 4 * (x + \mathbf{x\!d}) + 1 = \quad (5.67)$$

$$5 * (x^2 + 2 * x * \mathbf{x\!d} + (\mathbf{x\!d})^2) + 4 * x + 4 * (\mathbf{x\!d}) + 1 \quad (5.68)$$

然而，根据定义 $\mathbf{(d \; ^{2})} = 0$，因此该项消失。
重新排列各项：

$$(5 * x^2 + 4 * x + 1) + (10 * x + 4)\mathbf{x\!d} \quad \quad \quad \quad \quad (5.69)$$

但既然 $g (x ) = (5 * x^{2} + 4 * x + 1)$，那么：

$$g(x + \mathbf{x\!d}) = g(x) + g^{\prime}(x)\mathbf{x\!d} \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad (5.70)$$

3 使用 $DN$ 在 $x = 5$ 处评估函数 $g (x)$，我们得到：

$$
\begin{array}{l}
g(x = 5) = (5 * 5^{2} + 4 * 5 + 1) + (10 * 5 + 4)\mathbf{x\!d} = \\
\quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad 146 + (54)\mathbf{x\!d}
\end{array} 
\quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad (5.71)
$$

4 5.18 中的代码片段使用 Autograd 实现了该函数。

```python
1 import autograd.numpy as np
2 from autograd import grad
3 x = np.array([5.0], dtype=float)
4 def f1 (x):
5     return 5* x**2 + 4* x + 1
6 grad_f1 = grad(f1)
7 print (f1(x)) #> 146.0
8 print (grad_f1(x)) #> 54.0
```

![](img/574135cb1d7125b50cf484d943cdd676_180_0.png)

## 5.3.14 前向模式自动微分

$$
g(x)=A+B*\ln(C)\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad(5.72)
$$

2 对于对数函数：

$$
\frac{d}{dx}\ln(x)=\frac{1}{x}\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad(5.73)
$$

*因此，函数 g(x) 的偏导数为：*
$$
\begin{aligned}
&\frac{\partial f}{\partial A}=1\\
&\frac{\partial f}{\partial B}=\ln(C)\\
&\frac{\partial f}{\partial C}=B*\frac{1}{C}
\end{aligned}\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad(5.74)
$$

## SOL-129 CH.SOL-5.30. 答案如下：

1 正确。两个方向产生的结果完全相同。

2 正确。反向模式比前向模式自动微分效率更高（为什么？）。

3 正确。

4 正确。

## SOL-130 CH.SOL-5.31.

*答案如下：*

1 该函数为

$$f\left(x_1, x_2\right)=x_1 x_2+\ln\left(x_1\right) \tag{5.75}$$

2 前向模式自动微分对应的图如下：

![](img/574135cb1d7125b50cf484d943cdd676_182_0.png)

3 偏导数为：

$$\frac{\partial f}{\partial x_1}=x_2-\frac{1}{\left(x_1\right)} \quad \frac{\partial f}{\partial x_2}=x_1 \tag{5.76}$$

## 5.3.15 前向模式自动微分表格构建

### SOL-131 CH.SOL-5.32.
答案如下：

1 带有中间值的图如图 5.20 所示。

![](img/574135cb1d7125b50cf484d943cdd676_183_0.png)

图 5.20：5.1 中 $ g(x_1, x_2) $ 的导数图

2 $ g(x_1, x_2) = \ln(x_1) + x_1x_2 $ 在 $ (x_1, x_2) = (e^2, \pi) $ 处的前向模式自动微分。

前向模式函数求值：
$v_{-1} = x_1 = e^2$
$v_0 = x_2 = \pi$
$v_1 = \ln v_{-1} = \ln(e^2) = 2$
$v_2 = v_{-1} \times v_0 = e^2 \times \pi = 23.2134$
$v_3 = v_1 + v_2 = 2 + 23.2134 = 25.2134$
$f = v_3 = \approx 25.2134$

表 5.1：$ v = g(x_1, x_2) = \ln(x_1) + x_1x_2 $ 在 $ (x_1, x_2) = (e^2, \pi) $ 处求值，并设置 $\dot{x}_1 = 1$ 以计算 $\frac{\partial g}{\partial x_1}$ 的前向模式自动微分表。

| 变量 | 值 |
| :--- | :--- |
| $v_{-1} = x_1$ | $e^2$ |
| $v_0 = x_2$ | $\pi$ |
| $v_1 = \ln v_{-1}$ | $\ln(e^2) = 2$ |
| $v_2 = v_{-1} \times v_0$ | $e^2 \times \pi = 23.2134$ |
| $v_3 = v_1 + v_2$ | $2 + 23.2134 = 25.2134$ |
| $f = v_3$ | $\approx 25.2134$ |

3 以下 Python 代码（5.21）证明了数值结果是正确的：

```python
1 import math
2 print(math.log(math.e**math.e) + math.e**math.e * math.pi)
3 > 25.2134
```

图 5.21：Python 代码 - 函数 $ g(x_1, x_2) $ 的自动微分

4 种子值指的是在计算图中传播之前，用于初始化因变量和自变量的值。例如：

$\dot{v}_{1} = \frac{\partial x_{1}}{\partial x_{1}} = 1$
$\dot{v}_{2} = \frac{\partial x_{2}}{\partial x_{1}} = 0$

因此，我们设置 $\dot{x}_{1} = 1$ 来计算 $\frac{\partial y}{\partial x_{1}}$。

5 在此，我们为 $f(x_{1}, x_{2}) = \ln(x_{1}) + x_{1}x_{2}$ 在 $(x_{1}, x_{2}) = (e^{2}, \pi)$ 处求值，并设置 $\dot{x}_{1} = 1$ 以计算 $\frac{\partial y}{\partial x_{1}}$ 的前向模式自动微分导数构建一个表格。在前向模式自动微分中，导数被称为切线。

在以下推导中，请注意，从数学上使用手动微分：

$$
\frac{\mathrm{d}}{\mathrm{d} x_{1}}\left[\ln(x_1) + x_{2}x_1\right] = \frac{\mathrm{d}}{\mathrm{d} x_{1}}\left[\ln(x_{1})\right] + x_{2} \cdot \frac{\mathrm{d}}{\mathrm{d} x_{1}}\left[x_{1}\right] = \frac{1}{x_{1}} + x_{2} \cdot 1 = \frac{1}{x_{1}} + x_{2}
$$

$\dot{v}_{1} = \frac{1}{v_{-1}} * \dot{v}_{-1} = \dot{v}_{-1} / v_{-1} = \frac{1}{e^{2}} * 1 = 1 / e^{2}$.

前向模式自动微分导数求值：

$v_{-1} = x_1 = e^2$
$v_0 = x_2 = \pi$
$\dot{v}_{-1} = \dot{x}_1 = 1$
$\dot{v}_0 = \dot{x}_2 = 0$
$\dot{v}_1 = \dot{v}_{-1}/v_{-1} = 1/e^2$
$\dot{v}_2 = \dot{v}_{-1} \times v_0 + \dot{v}_0 \times v_{-1} = 1 \times \pi + 0 \times e^2 = \pi$
$\dot{v}_4 = \dot{v}_1 + \dot{v}_2 = 1/e^2 + \pi$
$\dot{f} = \dot{v}_4 = 1/e^2 + \pi \approx 3.2769$

表 5.3：$v=g(x_1,x_2)=\ln(x_1)+x_1x_2$ 在 $(x_1,x_2)=(e^2,\pi)$ 处求值，并设置 $\dot{x}_1=1$（此处提及种子值：1）以计算 $\frac{\partial y}{\partial x_1}$ 的前向模式自动微分表。

| 变量 | 值 | 切线值 |
| :--- | :--- | :--- |
| $v_{-1} = x_1$ | $e^2$ | $\dot{v}_{-1} = 1$ |
| $v_0 = x_2$ | $\pi$ | $\dot{v}_0 = 0$ |
| $v_1 = \ln v_{-1}$ | $2$ | $\dot{v}_1 = 1/e^2$ |
| $v_2 = v_{-1} \times v_0$ | $23.2134$ | $\dot{v}_2 = \pi$ |
| $v_4 = v_1 + v_2$ | $25.2134$ | $\dot{v}_4 = 1/e^2 + \pi$ |
| $f = v_4$ | $\approx 25.2134$ | $\dot{f} \approx 3.2769$ |

6 以下 Python 代码（5.22）证明了数值结果是正确的：

```python
import autograd.numpy as np
from autograd import grad
import math

x1 = math.e**math.e
x2 = math.pi

def f1 (x1,x2):
 return (np.log(x1) + x1* x2)

grad_f1 = grad(f1)

print (f1(x1,x2)) # 25.2134
print(grad_f1(x1,x2)) # 3.2769
```

图 5.22：Python 代码。函数 g(x1,x2) 的自动微分

## 5.3.16 符号微分

## 5.3.17 简单微分

### SOL-132 CH.SOL-5.33.

答案如下：

1 数值微分等近似方法存在数值不稳定性与截断误差。

2 在符号微分中，会计算出函数导数的符号表达式。这种方法相当缓慢，且需要解析和操作符号。例如，数字 $\sqrt{2}$ 在 SymPy 中表示为对象 Pow(2,1/2)。由于 SymPy 采用精确表示，Pow(2,1/2)*Pow(2,1/2) 将始终等于 2。

### SOL-133 CH.SOL-5.34.

1 首先：

```python
import sympy
sympy.init_printing()
from sympy import Symbol
from sympy import diff, exp, sin, sqrt
y = Symbol('y')
y = sympy.Symbol('y')

sigmoid = 1 / (1 + sympy.exp(-y))
```

图 5.23：SymPy 中的 Sigmoid

2 其次：

```python
sig_der = sympy.diff(sigmoid, y)
```

图 5.24：SymPy 中的 Sigmoid 梯度

3 第三：

```python
sig_der.evalf(subs={y: 0})
> 0.25
```

图 5.25：SymPy 中的 Sigmoid 梯度

4 该图像绘制在图 5.26 中。

```python
p = sympy.plot(sig_der);
```

![](img/574135cb1d7125b50cf484d943cdd676_187_0.png)

图 5.26：SymPy 中 Sigmoid() 函数的梯度
