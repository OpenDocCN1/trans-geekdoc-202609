
# 向量值函数的导数

$$
\begin{matrix} 
Df f(x) = f f^{\prime}(x) = \frac{df f}{dx} = \begin{bmatrix} \frac{df_{1}}{dx} \\ \frac{df_{2}}{dx} \\ \vdots \\ \frac{df_{m}}{dx} \\ \end{bmatrix} \in \mathbb{R}^{m \times 1} 
\end{matrix}
$$

向量值函数的导数是一个包含 m 个元素的向量。

如果向量值函数的自变量 *x* 是一个包含多个变量的向量，这样的向量值函数称为多元向量值函数。设自变量个数为 n，函数个数为 m。这是一个从 $\mathbb{R}^{(n)}$ 到 $\mathbb{R}^{(m)}$ 的映射（变换） **f** : $\mathbb{R}^{(n)} \to \mathbb{R}^{(m)}$。输入 n 个自变量的值，输出 m 个实数。

多元向量值函数的每个函数 $f_i(x)$ 都是一个多元函数。在某点 *x* 处，如果每个函数 $f_i(x)$ 都有关于 *x* 的梯度，将这些梯度向量堆叠在一起得到一个矩阵，称为雅可比矩阵：

$$
\begin{matrix} 
Df f(x) = f f^{\prime}(x) = \frac{df f}{dx} = \begin{bmatrix} 
\frac{\partial f_{1}}{\partial x_{1}} & \frac{\partial f_{1}}{\partial x_{2}} & \cdots & \frac{\partial f_{1}}{\partial x_{n}} \\
\frac{\partial f_{2}}{\partial x_{1}} & \frac{\partial f_{2}}{\partial x_{2}} & \cdots & \frac{\partial f_{2}}{\partial x_{n}} \\
\vdots & \vdots & \ddots & \\
\frac{\partial f_{m}}{\partial x_{1}} & \frac{\partial f_{m}}{\partial x_{2}} & \cdots & \frac{\partial f_{m}}{\partial x_{n}} \\
\end{bmatrix} \in \mathbb{R}^{m \times n}
\end{matrix}
$$

这是一个 $m \times n$ 矩阵，其中每一行是一个函数的梯度。

通常，自变量和向量值函数写作列向量，每个函数的梯度写作行向量。但本书将自变量和向量值函数都写成行向量的形式，即：

$f(x) = (f_1(x), f_2(x), \cdots, f_m(x))$

$x = (x_1, x_2, \cdots, x_n)$

但此时雅可比矩阵为：

$$
\begin{matrix} 
Df f(x) = f f^{\prime}(x) = \frac{df f}{dx} = \begin{bmatrix} 
\frac{\partial f_{1}}{\partial x_{1}} & \frac{\partial f_{2}}{\partial x_{1}} & \cdots & \frac{\partial f_{m}}{\partial x_{1}} \\
\frac{\partial f_{1}}{\partial x_{2}} & \frac{\partial f_{2}}{\partial x_{2}} & \cdots & \frac{\partial f_{m}}{\partial x_{2}} \\
\vdots & \vdots & \ddots & \\
\frac{\partial f_{1}}{\partial x_{n}} & \frac{\partial f_{2}}{\partial x_{n}} & \cdots & \frac{\partial f_{m}}{\partial x_{n}} \\
\end{bmatrix} \in \mathbb{R}^{n \times m}
\end{matrix}
$$

雅可比矩阵由不同多元实值函数的梯度向量累积而成，因此梯度的四则运算和链式法则也适用。

设 f, g 为从 $\mathbb{R}^{(n)}$ 到 $\mathbb{R}^{(m)}$ 的两个向量值函数，则：

$D(\alpha f + \beta g)(x) = \alpha Df(x) + \beta Dg(x)$

设 g 为从 $\mathbb{R}^{(m)}$ 到 $\mathbb{R}^{(k)}$ 的向量值函数，f 为从 $\mathbb{R}^{(k)}$ 到 $\mathbb{R}^{(n)}$ 的向量值函数。对于 $\mathbb{R}^{(m)}$ 中的点 *x*，设 $g(x)$ 的值为 *z*。如果向量值函数和自变量等均为列向量形式，则：

$(f \circ g)'(x) = D(f \circ g)(x) = f'(z)g'(x) = Df(z)Dg(x)$

如果向量值函数和自变量等均为行向量形式，则：

$(f \circ g)'(x) = D(f \circ g)(x) = g'(x)f'(z) = Dg(x)Df(z)$

向量 $x = (x_1, x_2, \cdots, x_n)$ 可以看作其自身的多元向量值函数，其导数为单位矩阵 $I$：

$$
\begin{matrix} 
\frac{dx}{dx} = \begin{bmatrix} 
1 & 0 & \cdots & 0 \\
0 & 1 & \cdots & 0 \\
\vdots & \vdots & \ddots & \\
0 & 0 & \cdots & 1 \\
\end{bmatrix} = I
\end{matrix}
$$

根据导数的四则运算规则，对于向量 *x* 和 *b*，$\nabla_x(\alpha x + \beta b) = \alpha I$。

在上述示例 4 中，如果将 $E(y, \hat{y})$ 视为 y 的函数，该函数可视为两个函数 $z = y - \hat{y}$ 和 $E(z) = \frac{1}{2}z^2$ 的复合函数。$E(y, \hat{y})$ 关于 y 的梯度为：

$E'(z) = z^T$

$z'(y) = (y - \hat{y})' = I$

$\nabla_y E(y, \hat{y}) = E'(z)z'(y) = z^T z'(y) = z^T I = z^T = (y - \hat{y})^T$

## 示例 5

设

$$
\begin{matrix} 
z(x) = \begin{bmatrix} z_1(x) \\ z_2(x) \\ \end{bmatrix} = \begin{bmatrix} 2x_1 + 4x_2 + 7x_3 \\ 3x_1 + 5x_2 + 4x_3 \\ \end{bmatrix}
\end{matrix}
$$

是 *x* 的函数，且

$y = \begin{bmatrix} 4z_1 + 3z_2 \\ \end{bmatrix}$

是 *z* 的函数，则 $f(x) = y(z(x))$ 是 $y(z)$ 和 $z(x)$ 的复合函数，根据复合函数求导规则，有：

$$
\begin{matrix} 
f'(x) = y'(z)z'(x) = (4,3)\begin{bmatrix} 2 & 4 & 7 \\ 3 & 5 & 4 \\ \end{bmatrix} = (17,31,40)
\end{matrix}
$$

展开 $f(x)$ 的完整表达式：

$f(x) = 4(2x_1 + 4x_2 + 7x_3) + 3(3x_1 + 5x_2 + 4x_3) = 17x_1 + 31x_2 + 40x_3$

可以验证上述结果是正确的。

如果约定梯度写成列向量形式，链式法则将按相反顺序书写：

$$
\begin{matrix} 
y'(z) = \begin{bmatrix} 4 \\ 3 \\ \end{bmatrix} \quad 
z'(x) = \begin{bmatrix} 2 & 3 \\ 4 & 5 \\ 7 & 4 \\ \end{bmatrix} \quad 
f'(x) = z'(x)y'(z) = \begin{bmatrix} 2 & 3 \\ 4 & 5 \\ 7 & 4 \\ \end{bmatrix}\begin{bmatrix} 4 \\ 3 \\ \end{bmatrix} = \begin{bmatrix} 17 \\ 31 \\ 40 \\ \end{bmatrix}
\end{matrix}
$$

在今后推导这些公式时，必须注意梯度等向量是列向量还是行向量。

## 示例 6

$$
\begin{matrix} 
z = \begin{bmatrix} z_1 & z_2 & \cdots & z_n \\ \end{bmatrix} = \begin{bmatrix} x_1 & x_2 & \cdots & x_m \\ \end{bmatrix} \cdot \begin{bmatrix} 
w_{11} & w_{12} & \ldots & w_{1n} \\
w_{21} & w_{22} & \ldots & w_{2n} \\
\vdots & \vdots & \ddots & \vdots \\
w_{m1} & w_{m2} & \ddots & w_{mn} \\
\end{bmatrix} \\
= \begin{bmatrix} 
w_{11} * x_1 + w_{21} * x_2 + \cdots + w_{m1} * x_m, &
w_{12} * x_1 + w_{22} * x_2 + \cdots + w_{m2} * x_m, &
\cdots, &
w_{1n} * x_1 + w_{2n} * x_2 + \cdots + w_{mn} * x_m
\end{bmatrix}
\end{matrix}
$$

因为 $\frac{\partial z_i}{\partial x_j} = w_{ji}$，所以 $\frac{\partial z_i}{\partial x} = w_{.i}$ 是矩阵 $W$ 的第 i 列，故 $\frac{\partial z}{\partial x} = W$。

如果还有另一个变量 *y*，*z* 关于 *y* 的梯度为 $\frac{dy}{dz} = (\frac{\partial y}{\partial z_1}, \frac{\partial y}{\partial z_2}, \cdots, \frac{\partial y}{\partial z_n})^T$，则
